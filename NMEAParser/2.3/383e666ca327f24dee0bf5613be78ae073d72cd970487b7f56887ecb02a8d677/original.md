```
struct GST <: NMEAString
```

Position error statistics.

# Fields

  * `system::String`: GNSS system identifier (e.g., GPS, GLONASS, GALILEO, Combined).
  * `time::Float64`: Time in seconds.
  * `rms::Float64`: RMS value of the pseudorange residuals; includes carrier phase residuals during periods of RTK (float) and RTK (fixed) processing
  * `semi_major_error::Float64`: Error ellipse semi-major axis 1-sigma error, in meters
  * `semi_minor_error::Float64`: Error ellipse semi-minor axis 1-sigma error, in meters
  * `orientation_error::Float64`: Error ellipse orientation, degrees from true north
  * `latitude_error::Float64`: Latitude 1-sigma error, in meters
  * `longitude_error::Float64`: Longitude 1-sigma error, in meters
  * `height_error::Float64`: Height 1-sigma error, in meters
  * `valid::Bool`: Flag indicating the validity of the data.

Example String: :GPGST,172814.0,0.006,0.023,0.020,273.6,0.023,0.020,0.031*6A
