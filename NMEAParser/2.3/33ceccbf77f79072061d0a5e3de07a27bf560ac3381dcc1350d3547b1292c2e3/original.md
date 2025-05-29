```
struct DTM <: NMEAString
```

Datum Reference (DTM)

This NMEA data type represents information about a datum reference.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `local_datum_code::String`: Local datum code.
  * `local_datum_subcode::String`: Local datum subcode.
  * `lat_offset::Float64`: Latitude offset in meters.
  * `long_offset::Float64`: Longitude offset in meters.
  * `alt_offset::Float64`: Altitude offset in meters.
  * `ref_datum::String`: Reference datum.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
DTM(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = DTM(["DTM", "W84", "W", "0.5", "W", "1.0", "M", "W84"])
```
