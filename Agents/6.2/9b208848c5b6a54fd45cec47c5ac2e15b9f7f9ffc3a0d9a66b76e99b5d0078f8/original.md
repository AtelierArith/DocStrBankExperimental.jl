```
nearby_agents(agent, model::ABM, r = 1; kwargs...) -> agent
```

Return an iterable of the agents near the position of the given `agent`.

The value of the argument `r` and possible keywords operate identically to [`nearby_ids`](@ref).
