```
set_speed(sp::SerialPort, baudrate::Integer)
```

Set the data signalling rate, or the reciprocal duration of one data bit, in bits/s. The set of values supported depends on the UART hardware, but typically includes e.g. 9600, 19200 and 115200.

Raise an `ErrorException` if `bps` is not a value supported by the driver or hardware.
