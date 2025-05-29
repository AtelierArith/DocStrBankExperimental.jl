```
struct VTG <: NMEAString
```

Track Made Good and Ground Speed (VTG)

This NMEA data type represents information about the track made good (course) and ground speed.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `CoG_true::Float64`: Course over ground in true degrees.
  * `CoG_mag::Float64`: Course over ground in magnetic degrees.
  * `SoG_knots::Float64`: Speed over ground in knots.
  * `SoG_kmhr::Float64`: Speed over ground in kilometers per hour.
  * `mode::Char`: Mode indicator ('A' for autonomous mode).
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
VTG(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = VTG(["VTG", "90.0", "T", "45.0", "M", "5.0", "K", "A"])
```
