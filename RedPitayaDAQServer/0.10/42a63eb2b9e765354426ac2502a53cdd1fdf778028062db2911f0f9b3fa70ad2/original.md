```
RedPitaya(ip [, port = 5025, dataPort=5026, isMaster = false])
```

Construct a `RedPitaya`.

During the construction the connection is established and the calibration values are loaded from the RedPitayas EEPROM. Throws an error if a timeout occurs while attempting to connect.

# Examples

```julia
julia> rp = RedPitaya("192.168.1.100");

julia> decimation!(rp, 8)
true

julia> decimation(rp)
8
```
