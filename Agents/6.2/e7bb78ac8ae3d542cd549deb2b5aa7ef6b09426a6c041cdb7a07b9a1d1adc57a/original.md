```
get_spatial_index(pos, property::AbstractArray, model::ABM)
```

Convert the continuous agent position into an appropriate `index` of `property`, which represents some discretization of a spatial field over a [`ContinuousSpace`](@ref).

The dimensionality of `property` and the continuous space do not have to match. If `property` has lower dimensionality than the space (e.g. representing some surface property in 3D space) then the front dimensions of `pos` will be used to index.
