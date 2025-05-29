```
random_nearby_agent(agent, model::ABM, r = 1, f = nothing, alloc = false; kwargs...) → agent
```

Return a random agent near the position of the given `agent` or `nothing` if no agent is nearby.

The value of the argument `r` and possible keywords operate identically to [`nearby_ids`](@ref).

A filter function `f(agent)` can be passed so that to restrict the sampling on only those agents for which the function returns `true`. The argument `alloc` can be used if the filtering condition is expensive since in this case the allocating version can be more performant. `nothing` is returned if no nearby agent satisfies `f`.

For discrete spaces, use [`random_agent_in_position`](@ref) instead to return a random agent at a given position.
