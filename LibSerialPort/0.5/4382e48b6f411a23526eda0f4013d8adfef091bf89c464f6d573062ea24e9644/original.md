The `LibSerialPort` module provides access to [serial ports](https://en.wikipedia.org/wiki/Serial_port) ([UARTs](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter) or USB/Bluetooth devices that emulate their operating-system interface) using the portable C library [libserialport](http://sigrok.org/wiki/Libserialport).

It defines the `SerialPort` type, which is returned by `LibSerialPort.open`. This is a subtype of `Base.IO` and can therefore be used like a file handle, using many of the same `read`, `write`, `print`, etc. methods defined for `Base.IO`.

# Example

```
using LibSerialPort

list_ports()
ports = get_port_list()

sp = LibSerialPort.open("/dev/ttyUSB0", 115200)
set_flow_control(sp)
sp_flush(sp, SP_BUF_BOTH)
write(sp, "hello\n")
println(readline(sp))
close(sp)
```
