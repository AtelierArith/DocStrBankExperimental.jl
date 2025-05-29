```
struct GLL <: NMEAString
```

Geographic Latitude and Longitude (GLL)

This NMEA data type represents information about geographic latitude and longitude.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `latitude::Float64`: Latitude in decimal degrees.
  * `longitude::Float64`: Longitude in decimal degrees.
  * `time::Float64`: Time in seconds.
  * `status::Bool`: Status indicator (true if valid fix, false otherwise).
  * `mode::Char`: Mode indicator ('A' for autonomous mode).
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
GLL(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = GLL(["GLL", "12.3456", "N", "98.7654", "W", "123456", "A"])
```
