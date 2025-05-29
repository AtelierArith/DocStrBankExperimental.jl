```
struct GGA <: NMEAString
```

GPS Fix Data (GGA)

This NMEA data type represents information about the GPS fix, including latitude, longitude, altitude, number of satellites, and accuracy measures.

# Fields

  * `system::String`: GPS, GLONASS, GALILEO, or Combined.
  * `time::Float64`: Time in seconds.
  * `latitude::Float64`: Latitude in decimal degrees.
  * `longitude::Float64`: Longitude in decimal degrees.
  * `fix_quality::String`: Quality of the fix.
  * `num_sats::Int`: Number of satellites used in the fix.
  * `HDOP::Float64`: Horizontal Dilution of Precision.
  * `altitude::Float64`: Altitude above mean sea level (MSL) in meters.
  * `geoidal_separation::Float64`: Geoidal separation in meters.
  * `age_of_differential::Float64`: Age of the differential data.
  * `diff_reference_id::Int`: Differential reference station ID.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
GGA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = GGA(["GGA", "123456", "123.456", "N", "987.654", "W", "1", "8", "0.9", "123.4", "M", "54.3", "M", "1"])
```
