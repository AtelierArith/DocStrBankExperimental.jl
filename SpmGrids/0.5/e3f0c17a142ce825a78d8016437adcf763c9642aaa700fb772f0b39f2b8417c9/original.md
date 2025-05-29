```
has_channel(grid::SpmGrid, name::AbstractString; bwd::Bool=false)::Bool
```

Returns `true` if channel `name` is present in the grid. If `bwd` is `true`, the checks for the existance of the bwd channel.
