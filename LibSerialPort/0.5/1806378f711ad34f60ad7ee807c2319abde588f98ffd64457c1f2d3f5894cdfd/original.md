```
set_read_timeout(sp::SerialPort, seconds::Real)
```

Set a read timeout limit of `t` > 0 seconds for the total (cumulative) time that subsequently called blocking read functions can wait before a `Timeout` exception is thrown.

# Example

```
sp=LibSerialPort.open("/dev/ttyUSB0", 115200)
# wait until either two lines have been received
# or 10 seconds have elapsed
set_read_timeout(sp, 10)
try
    line1 = readuntil(sp, '\n')
    line2 = readuntil(sp, '\n')
catch e
    if isa(e, LibSerialPort.Timeout)
        println("Too late!")
    else
        rethrow()
    end
end
clear_read_timeout(sp)
```

See also: [`clear_read_timeout`](@ref), [`set_write_timeout`](@ref)
