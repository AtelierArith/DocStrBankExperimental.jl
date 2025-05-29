```
struct GBS <: NMEAString
```

GNSS Satellite Fault Detection (GBS)

This NMEA data type represents information about satellite fault detection, including error estimates and probabilities.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `time::Float64`: Time in seconds.
  * `lat_error::Float64`: Latitude error estimate.
  * `long_error::Float64`: Longitude error estimate.
  * `alt_error::Float64`: Altitude error estimate.
  * `failed_PRN::Int`: PRN of the failed satellite.
  * `prob_of_missed::Float64`: Probability of missed detection.
  * `excluded_meas_err::Float64`: Excluded measurement error.
  * `standard_deviation::Float64`: Standard deviation of the measurements.
  * `valid::Bool`: Flag indicating the validity of the data.

# Constructor

```julia
GBS(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# Examples

```julia
data = GBS(["GBS", "123456", "0.1", "0.2", "0.3", "5", "0.01", "0.05", "0.02"])
```
