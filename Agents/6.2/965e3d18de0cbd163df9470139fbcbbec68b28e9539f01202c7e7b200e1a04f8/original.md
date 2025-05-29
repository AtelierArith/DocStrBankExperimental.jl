```
random_nearby_id(agent, model::ABM, r = 1, f = nothing, alloc = false; kwargs...) → id
```

Return the `id` of a random agent near the position of the given `agent`.

Return `nothing` if no agents are nearby.

The value of the argument `r` and possible keywords operate identically to [`nearby_ids`](@ref).

A filter function `f(id)` can be passed so that to restrict the sampling on only those ids for which the function returns `true`. The argument `alloc` can be used if the filtering condition is expensive since in this case the allocating version can be more performant. `nothing` is returned if no nearby id satisfies `f`.

For discrete spaces, use [`random_id_in_position`](@ref) instead to return a random id at a given position.

This function, as all the other methods which sample from lazy iterators, uses an optimized algorithm which doesn't require to collect all elements to just sample one of them.
