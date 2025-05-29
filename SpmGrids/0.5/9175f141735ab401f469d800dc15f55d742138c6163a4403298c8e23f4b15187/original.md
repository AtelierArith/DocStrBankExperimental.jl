```
add_parameter!(grid::SpmGrid, name::AbstractString, unit::AbstractString,
    data::AbstractArray{Float64}; force::Bool=false)::Nothing
```

Adds a generated parameter with `name`, `unit` and `data` to the `grid`. The `data` must be of the same size as parameter data in the `grid`, i.e. `grid.pixelsize`. The `name` cannot be the same as names in the original parameter names. If the `name` exists in the generated parameter names, it will be overwritten. If `force` is `true`, then the consistency checks for name and dimensions are overriden.
