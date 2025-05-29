```
is_string_supported(nmea_string::AbstractString)
```

Check if the input NMEA string type is supported.

# Arguments

  * `nmea_string::AbstractString`: The NMEA string to be checked.

# Returns

  * `Bool`: `true` if the NMEA string is supported, `false` otherwise.

# Example

```julia
julia> is_string_supported("$GPGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,*47")
true
```
