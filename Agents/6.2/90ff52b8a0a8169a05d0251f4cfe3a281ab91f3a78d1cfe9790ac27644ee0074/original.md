```
random_id_in_position(pos, model::ABM, [f, alloc = false]) → id
```

Return a random id in the position specified in `pos`.

A filter function `f(id)` can be passed so that to restrict the sampling on only those agents for which the function returns `true`. The argument `alloc` can be used if the filtering condition is expensive since in this case the allocating version can be more performant. `nothing` is returned if no nearby position satisfies `f`.

Use [`random_nearby_id`](@ref) instead to return the `id` of a random agent near the position of a given `agent`.
