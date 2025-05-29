```
get_spatial_property(pos, property::AbstractArray, model::ABM)
```

Convert the continuous agent position into an appropriate `index` of `property`, which represents some discretization of a spatial field over a [`ContinuousSpace`](@ref). Then, return `property[index]`. To get the `index` directly, for e.g. mutating the `property` in-place, use [`get_spatial_index`](@ref).
