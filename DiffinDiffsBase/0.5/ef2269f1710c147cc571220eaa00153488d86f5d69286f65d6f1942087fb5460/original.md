```
lead(panel::PanelStructure, v::AbstractArray, l::Integer=1; default=missing)
```

Return a vector of `l`th lead values of `v` with missing values filled with `default`. The `panel` structure is respected. See also [`ilead!`](@ref) and [`lag`](@ref).
