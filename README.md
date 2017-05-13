# muslx32toolkit
BASH Scripts for Gentoo Linux to build stage3 and stage4 images using crossdev for the muslx32 platform

note: This is currently being actively developed as of 20170507 from the written instructions to automated scripts to avoid human error.

note: The scripts rely on stable packages.  ~amd64 keyworded packages are not supported.  If you want ~amd64 support you must manually update the patches yourself.

The scripts use an interactive checkpoint system so you can edit and return back to that step them if they fail.  You may need to edit the config file to properly edit packages to unmask or and use, or specific files/versions to use.

Step 0: Download the stage3 tarball and the portage snapshot contained in the config file.  It is important that you make sure you download the files in a folder that is either a mounted partition or a new folder.

Step 1: chmod +x prepare

Step 2: Run ./prepare

Step 3: Move the muslx32toolkit folder into the same folder as the stage3 and portage snapshot

Step 4: Run ./build-crossdev-toolchain `<full-path-containing-both-stage3-and-portage-tarball>`

(chroot)

Step 5: Run ./create-stage3 in muslx32toolkit

(chroot)

Step 6: Run ./create-stage4 in muslx32toolkit

(chroot)

Step 7: Modify /etc/fstab

Step 8: Modify bootloader and install it

Step 9: Add users

Step 10: Add root password

Step 11: Perform any additions to your stage4 image

## Notes

Before running ./create-stage4 you may need to check the existance of make.conf.native make.conf.cross in your /etc/portage folder.  If they do not exist, chroot out and run ./create-stage3 and regenerate the make.conf.cross and make.conf.native.  Then chroot back in the /usr/<profile> or through ./create-stage3 script

## License

The files in this package are licensed under GPL version 2 or newer.
