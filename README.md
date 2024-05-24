## Инициализация:

### 1) Load kernel module:
*vim /etc/modules:*
```
sudo modprobe usbserial vendor=0x0403 product=0x6001
```
---
### 2) Create FIFO channel:
`sudo mknod /dev/ttyUSB0 c 188 0`

`c` - symbol (non-bufferized) special file

`188` - major node number

`0` -minor  node number

To get the major/minor numbers of a connected device you can cat the device data:
`cat /sys/class/tty/ttyUSB0/uevent`

---
###  3) Setup privileges:
`sudo chmod 777 /dev/ttyUSB0`
### 4) Setup ownership:
`sudo chown <username> /dev/ttyUSB0`

## Подключение:

### В терминальной сессии:
`sudo minicom -b 9600 -o -D /dev/ttyUSB0`

`-b` - baudrate (скорость передачи данных), default value: 9600
 [Datasheet](obsidian://open?vault=Mass%20storage&file=PAYWHALE%2FMicrosoft%20Word%20-%20SIM800C_Hardware_Design_V1.02-150427.doc%20-%20SIM800C_Hardware_Design_V1.02.pdf) : Autobauding supports the following baud rates: 1200, 2400, 4800, 9600, 19200, 38400, 57600 and 115200bps
 `-o` - option, set an option
 `-D` - Device, select device
