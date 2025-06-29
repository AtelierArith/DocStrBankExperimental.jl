```
C_iio_create_context_from_uri(uri)
```

Create a context from a URI description.

# Parameters

  * `uri::String` : A URI describing the context location

# Returns

  * On success, a pointer to a iio_context structure
  * On failure, if the assertions are enabled, an error is thrown.
  * On failure, if the assertions are disabled, NULL is returned.

# NOTE

The following URIs are supported based on compile time backend support:

  * Local backend, "local:":   Does not have an address part. For example "local:"
  * XML backend, "xml:"   Requires a path to the XML file for the address part. For example "xml:/home/user/file.xml"
  * Network backend, "ip:"   Requires a hostname, IPv4, or IPv6 to connect to a specific running IIO Daemon or no address part for automatic discovery when library is compiled with ZeroConf support. For example "ip:192.168.2.1", or "ip:localhost", or "ip:" or "ip:plutosdr.local"
  * USB backend, "usb:"   When more than one usb device is attached, requires bus, address, and interface parts separated with a dot. For example "usb:3.32.5". Where there is only one USB device attached, the shorthand "usb:" can be used.
  * Serial backend, "serial:" requires :

      * a port (/dev/ttyUSB0),
      * baud_rate (default 115200)
      * serial port configuration

          * data bits (5 6 7 8 9)
          * parity ('n' none, 'o' odd, 'e' even, 'm' mark, 's' space)
          * stop bits (1 2)
          * flow control (' ' none, 'x' Xon Xoff, 'r' RTSCTS, 'd' DTRDSR)
      * For example "serial:/dev/ttyUSB0,115200" or "serial:/dev/ttyUSB0,115200,8n1"

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gafdcee40508700fa395370b6c636e16fe)
