```
get_parameter(grid::SpmGrid, name::AbstractString,
    x_index::GridRange=:, y_index::GridRange=:; view::Bool=true)::Union{Array{Float64},SubArray{Float64}}
```

Returns the value for parameter `name` at the point(s)specified by `x_index`, `y_index`. If `view` is `true` (default), then a view(@ref Base.view) is returned , otherwise a copy.
