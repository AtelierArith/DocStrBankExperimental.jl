```
add_channel!(grid::SpmGrid, name::AbstractString, unit::AbstractString,
    data::AbstractArray{Float64}; force::Bool=false)::Nothing::Nothing
```

Adds a generated channel with `name`, `unit` and `data` to the `grid`. The `data` must be of the same size as channel data in the `grid`, i.e. `grid.points` x `grid.pixelsize...`. The `name` cannot be the same as names in the original channel names. If the `name` exists in the generated channel names, it will be overwritten. If `force` is `true`, then the consistency checks for name and dimensions are overriden.
