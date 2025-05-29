```
struct GSV <: NMEAString
```

Satellites in View (GSV)

This NMEA data type represents information about the satellites in view and their signal strength.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `msg_total::Int`: Total number of GSV messages for this cycle.
  * `msg_num::Int`: Number of this GSV message.
  * `sat_total::Int`: Total number of satellites in view.
  * `SV_data::Vector{SVData}`: Vector of satellite data, each containing PRN, elevation, azimuth, and SNR.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
GSV(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = GSV(["GSV", "3", "1", "9", "1", "01", "30", "45", "20", "02", "60", "180", "25", "03", "15", "300", "15"])
```
