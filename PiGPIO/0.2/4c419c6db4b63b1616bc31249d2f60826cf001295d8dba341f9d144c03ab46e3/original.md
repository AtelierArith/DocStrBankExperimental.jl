```
Pi(; host = get(ENV, "PIGPIO_ADDR", ""),
   port = get(ENV, "PIGPIO_PORT", 8888))
```

Grants access to a Pi's GPIO.

`host` is the host name of the Pi on which the pigpio daemon is  running.  The default is localhost unless overridden by  the PIGPIO_ADDR environment variable.

`port` is the port number on which the pigpio daemon is listening.  The default is 8888 unless overridden by the PIGPIO_PORT  environment variable.  The pigpio daemon must have been  started with the same port number.

This connects to the pigpio daemon and reserves resources to be used for sending commands and receiving notifications.

An instance attribute `connected` may be used to check the success of the connection.  If the connection is established successfully `connected` will be true, otherwise false.

```julia
pi = PiGPIO.Pi()                           # use defaults
pi = PiGPIO.Pi(host = "mypi")              # specify host, default port
pi = PiGPIO.Pi(host = "mypi", port = 7777) # specify host and port

pi = PiGPIO.Pi()                           # exit script if no connection
if !pi.connected
   exit()
end
```
