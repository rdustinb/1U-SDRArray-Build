# 1U-SDRArray-Build
My notes and any design files pertaining to building a 1U Raspberry Pi based array of RTLSDRs.

## Design Concepts

### Raspberry Pi USB Power
The Raspberry Pi 4 can supply a total of 1.2A Max across all four USB ports.

The RTL-SDR [Datasheet](https://www.rtl-sdr.com/wp-content/uploads/2024/12/RTLSDR_V4_Datasheet_V_1_0.pdf) states that a single RTL-SDR v4 requires a typical 250-270mA. Unfortunately this is not a
maximum rating so I may have to experiment to determine if I can run 4 at full tilt and not brown out the USB bus
supply.

4x 270mA = 1.08A with 10% headroom (0.120A)

### Cooling
There are four chips on the Raspberry Pi 4 which would benefit from having a tall heat sink attached to it:

BCM2711 Processor - 14x14mm
9FD77 LPDDR4 RAM Chip - 14x10mm
VL805 USB 3.0 Controller - 8x8mm
MXL7704 DC to DC Converter - 5x5mm

There are two chips on each RTLSDR v4 board which would benefit from having a tall heat sink attached to it:

R828D Tuner with Low Noise Amplifier - 6x6mm
RTL2832U DVB-T COFDM Demodulator - 6x6mm

### Bill of Materials

1x Raspberry Pi 4, 8GB - $82.50
4x RTL-SDR v4 - $152
4x USBA 2ft Extension Cables - $24
[This](https://www.amazon.com/Nanxudyj-Extension-Extender-Transfer-Playstation/dp/B08M69BP2K/ref=sr_1_3?crid=270BRE1SM9Q2O&dib=eyJ2IjoiMSJ9.0a5HKT_kGKskgQfLHt4GlPizcGW6IYM5BuGxlrhkGq9kAeK1evlpPZsDqD4pTetUBz73-6xibAzADOTIq4gFA05t3Uu9et8l0x6le0eI5ea3DFHEjCpdZK5Akny4ctzoVWnfLu-3pcqd0RVZvgiodVzy4_rxX9JFWt22R45opLl_q55CxkJl_WZvyPvqXfoXG99J-yDVEpE0Ob3UAvFlhLyuPma6WxK3BJOL0qOigPs.lRz8biIwhqAgL79Rr5gHPc3tnAlYCxRQa6NTeK2S66o&dib_tag=se&keywords=usb%2Ba%2Bextension%2B2ft&qid=1751045655&sprefix=usb%2Ba%2Bextension%2B2ft%2Caps%2C165&sr=8-3&th=1) seems to be a good option, they run about $3/ft.
1U Project Chassis - $50
Two options available, [this](https://www.circuitspecialists.com/rackmount-enclosure-37-1u) or [this](https://www.redco.com/Redco-CH1-1U-Rackmount-Chassis-Box.html).
4x Noctua 40x20mm Fans - $60
It seems best to hook up these 5V fans to the GPIO 3.3V rail and they run a little quieter. Though some testing is
necessary to hear how loud they are running full tilt on the 5V rail.
Miscellaneous Heat Sinks - $30
USB Panel Mout - $15
The USBC Panel mount only needs to be used for power so there is no data bandwidth needs to this port. A good candidate
seems to be something like [this](https://www.amazon.com/PENGLIN-Coupler-Connector-Bulkhead-Extension/dp/B0B4VWZD7X/ref=sr_1_4?crid=2OXCWVIQEPDY3&dib=eyJ2IjoiMSJ9.AWs3zoEFMR88H7_ev8TX_1ZuhfwyslXVr6p4GIl6bmcLLKx9xwHUqjTMHiavICNIHr0dix5s_HyMFrQvK_QlkXO_-_jDw5TxoprCttPdujEogsMbHMv4J15lfeZnHQQ0lcYMI7LENp7BWEA6pb_9jtw3cwqHWqoGP2qVnbOifee_sJuEWRYOqpgrMyH_qffiE9DyRd2_ERE8uSJKEvFkY_zuUJDylXYXKDogctawJhQ.nH2UeQ37G5Sy2gk6V-J9yEm7djm0C-ztIFFhPkgupJ4&dib_tag=se&keywords=USBC%2BPanel%2BMount&qid=1751048464&sprefix=usbc%2Bpanel%2Bmount%2Caps%2C198&sr=8-4&th=1).


Total Cost - $415
