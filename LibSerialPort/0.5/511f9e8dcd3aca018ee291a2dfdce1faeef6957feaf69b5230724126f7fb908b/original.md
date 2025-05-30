```
set_write_timeout(sp::SerialPort, seconds::Real)
```

Set a write timeout limit of `t` > 0 seconds for the total (cumulative) time that subsequently called blocking read functions can wait before a `Timeout` exception is thrown.

# Example

```
sp=LibSerialPort.open("/dev/ttyUSB0", 300)
# wait until either 4000 periods have been
# passed on to the serial-port driver or
# 10 seconds have elapsed
set_write_timeout(sp, 10)
try
    for i=1:50 ; write(sp, '.' ^ 80); end
catch e
    if isa(e, LibSerialPort.Timeout)
        println("This took too long!")
    else
        rethrow()
    end
end
clear_write_timeout(sp)
```

See also: [`clear_write_timeout`](@ref), [`set_read_timeout`](@ref)
