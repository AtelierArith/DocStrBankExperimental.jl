```
struct RMC <: NMEAString
```

Recommended Minimum Navigation Information (RMC)

This NMEA data type represents recommended minimum navigation information.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `time::Float64`: Time in seconds of position fix.
  * `status::Bool`: Status indicator (true if active, false otherwise/void).
  * `latitude::Float64`: Latitude in decimal degrees.
  * `longitude::Float64`: Longitude in decimal degrees.
  * `sog::Float64`: Speed over ground in knots.
  * `cog::Float64`: track angle over ground in degrees.
  * `date::Date`: Day of the month.
  * `month::String`: Month of the year.
  * `year::String`: Year.
  * `magvar::Float64`: Magnetic variation.
  * `mode::Char`: Position system mode indicator (D=differential,A=autonomous,N=not valid,E=estimated/dead reckoning, M=manual input).
  * `navstatus::Char`: Navigational status. (S = Safe, C = Caution, U = Unsafe, V = Navigational status not valid).
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
RMC(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
nmeastr = "$GPRMC,123519,A,4807.038,N,01131.000,E,022.4,084.4,230394,003.1,W*6A"
data = RMC(["RMC", "123519", "A", "4807.038", "N", "01131.000", "E", "022.4", "084.4", "230394", "003.1", "W"], "GPS", true)

altstr = "$GNRMC,060512.00,A,3150.788156,N,11711.922383,E,0.0,,311019,,,A,V*1B"
```
