```
struct GSA <: NMEAString
```

GNSS DOP and Active Satellites (GSA)

This NMEA data type represents information about the GNSS Dilution of Precision (DOP) and the active satellites used for navigation.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `mode::Char`: Mode of operation (A = Automatic, M = Manual).
  * `current_mode::Int`: Operating mode (1 = Fix not available, 2 = 2D fix, 3 = 3D fix).
  * `sat_ids::Vector{Int}`: Vector of satellite IDs used in the fix.
  * `PDOP::Float64`: Position Dilution of Precision.
  * `HDOP::Float64`: Horizontal Dilution of Precision.
  * `VDOP::Float64`: Vertical Dilution of Precision.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
GSA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = GSA(["GSA", "M", "3", "1", "2", "3", "1.2", "0.9", "1.5"])
```
