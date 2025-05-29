```
random_nearby_position(pos, model::ABM, r=1, f = nothing, alloc = false; kwargs...) → position
```

Return a random position near the given position. Return `nothing` if the space doesn't allow for nearby positions.

The value of the argument `r` and possible keywords operate identically to [`nearby_positions`](@ref).

A filter function `f(pos)` can be passed so that to restrict the sampling on only those positions for which the function returns `true`. The argument `alloc` can be used if the filtering condition is expensive since in this case the allocating version can be more performant. `nothing` is returned if no nearby position satisfies `f`.
