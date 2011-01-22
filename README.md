  boot-scripts
=======

Some u-boot command scripts for Overo Tide and Beagleboard-xM boards. These 
boards don't have NAND to save u-boot customizations so a boot.scr file is used.

The behaviour to look for a file called 'boot.scr' is built into the default
bootloaders for these boards.

Overos and Beagleboards with NAND also look for the boot.scr file. It is sometimes
convenient with customers to give them a boot.scr rather then ask them to make
u-boot environment changes manually.

I'll add the xM scripts after some more testing.


make-boot-script.sh
------
Generates a boot.scr file from the command script file you pass as an argument.


Example Script Files
=======


tide-mmc-boot 
------
Overo Tide, simple MMC boot, no video, 720 MHz


tide-nfs-boot
------
Overo Tide, simple NFS boot, no video, 720 MHz, the IP addresses and NFS mount
point should be customized. 

If you are using an older expansion board without an EEPROM storing the
ethernet MAC, you will have to add a

setenv ethaddr xx:xx:xx:xx:xx:xx 

line to the command script. 

You can get a valid ethaddr by booting the tide-mmc-boot first and then checking
the ethaddr that the Linux driver uses.


el-mmc-boot
------
A customer script file for Overo. Sets aside some reserved memory for a camera 
driver. Also sets up i2c-bus speed.


el-nfs-boot
------
Same customer. A network booting script.



Customize U-Boot Config
======
An alternative to this boot.scr stuff is to modify the u-boot source code
directly with your customizations and rebuild it.

<u-boot-src>/include/configs/omap3_overo.h 

or 

<u-boot-src>/include/configs/omap3_beagle.h 


This will speed your boot times a little.

