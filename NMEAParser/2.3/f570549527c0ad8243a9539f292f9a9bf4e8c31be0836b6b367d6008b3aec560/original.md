```
nmea_parse(nmea_string::AbstractString; validate_checksum=true)
```

Parse an NMEA string and generate the corresponding NMEA type.

This function takes an NMEA sentence as input, validates the checksum if `validate_checksum` is set to `true`, and then parses the sentence based on the predefined headers and types in `NMEA_TYPES`.

# Arguments

  * `nmea_string::AbstractString`: The NMEA sentence to parse.
  * `validate_checksum::Bool`: Flag to indicate whether to validate the checksum (default is `true`).

# Returns

  * An instance of the appropriate NMEA type.

# Examples

```julia
result = nmea_parse("$GGA,123456,123.456,N,987.654,W,1,8,0.9,123.4,M,54.3,M,1,")
```
