```
nearby_positions(pos, model::ABM{<:DiscreteSpace}, r=1; kwargs...)
```

Return an iterable of all positions within "radius" `r` of the given `position` (which excludes given `position`). The `position` must match type with the spatial structure of the `model`.

The value of `r` and possible keywords operate identically to [`nearby_ids`](@ref).

This function only exists for discrete spaces with a finite amount of positions.

```
nearby_positions(position, model::ABM{<:OpenStreetMapSpace}; kwargs...) → positions
```

For [`OpenStreetMapSpace`](@ref) this means "nearby intersections" and operates directly on the underlying graph of the OSM, providing the intersection nodes nearest to the given position.
