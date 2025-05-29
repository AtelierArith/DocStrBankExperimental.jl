```
struct ZDA <: NMEAString
```

Time and Date (ZDA)

This NMEA data type represents information about the current time and date from a GNSS receiver.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `time::Float64`: Time in seconds.
  * `day::Int`: Day of the month.
  * `month::Int`: Month of the year.
  * `year::Int`: Year.
  * `zone_hrs::Int`: Time zone offset in hours.
  * `zone_mins::Int`: Time zone offset in minutes.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
ZDA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = ZDA(["ZDA", "123456", "15", "02", "2024", "5", "30"])
```
