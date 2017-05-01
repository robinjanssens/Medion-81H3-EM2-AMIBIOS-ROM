# Medion-81H3-EM2-AMIBIOS-ROM
BIOS ROM for Medion 81H3-EM2

## Programming the chip
To program the chip I used the SPI interface of a Raspberry Pi and [flashrom](https://www.flashrom.org/Flashrom) to program and verify. There are a lot of tutorials online to guide you through this process (e.g. [Win-Raid Forum](http://www.win-raid.com/t58f16-Guide-Recover-from-failed-BIOS-flash-using-Raspberry-PI.html) or [Libreboot docs](https://libreboot.org/docs/install/rpi_setup.html)).

### READ
Always write current image to file before overwriting it!

`sudo flashrom -r ./old.ROM -V -p linux_spi:dev=/dev/spidev0.0 -c "MX25L6406E/MX25L6408E"`

### WRITE
`sudo flashrom -w ./medion81H3EM2.ROM -V -p linux_spi:dev=/dev/spidev0.0 -c "MX25L6406E/MX25L6408E"`

## Source of ROM file
I read the corrupted bios file from the bios flash chip ([MX25L6406E datasheet](http://www.macronix.com/Lists/Datasheet/Attachments/5051/MX25L6406E,%203V,%2064Mb,%20v1.9.pdf)) and combined it with binary files found on the [Medion website](http://www.medion.com/be/nl/service/_lightbox/software_details.php?did=13978) using [UEFITOOL](http://www.majorgeeks.com/files/details/uefitool.html) to fix a broken workstation after a failed bios update.
