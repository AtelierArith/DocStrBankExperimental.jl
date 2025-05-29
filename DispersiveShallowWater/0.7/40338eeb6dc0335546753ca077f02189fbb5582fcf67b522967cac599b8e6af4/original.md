```
bathymetry_mild_slope = DispersiveShallowWater.BathymetryMildSlope()
```

A singleton struct indicating a variable bathymetry with mild-slope approximation. Typically, this means that some terms like $b_x^2$ are neglected.

See also [`bathymetry_flat`](@ref) and [`bathymetry_variable`](@ref).
