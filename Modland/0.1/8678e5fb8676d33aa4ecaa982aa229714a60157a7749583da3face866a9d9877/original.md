```
latlon_to_sinusoidal(lat::Float64, lon::Float64)::Tuple{Float64,Float64}
```

Convert latitude and longitude coordinates to sinusoidal projection coordinates.

# Arguments

  * `lat::Float64`: Latitude in degrees.
  * `lon::Float64`: Longitude in degrees.

# Returns

  * `Tuple{Float64, Float64}`: Sinusoidal projection coordinates (x, y).
