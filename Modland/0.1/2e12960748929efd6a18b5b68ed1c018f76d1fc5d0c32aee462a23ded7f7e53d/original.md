```
sinusoidal_to_modland(x::Float64, y::Float64)::String
```

Convert sinusoidal projection coordinates to MODIS land tile indices.

# Arguments

  * `x::Float64`: Sinusoidal x coordinate.
  * `y::Float64`: Sinusoidal y coordinate.

# Returns

  * `String`: MODIS land tile index in the format "hXXvYY".
