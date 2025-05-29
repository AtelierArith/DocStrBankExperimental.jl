```
empty_nearby_positions(pos, model::ABM{<:DiscreteSpace}, r = 1; kwargs...)
empty_nearby_positions(agent, model::ABM{<:DiscreteSpace}, r = 1; kwargs...)
```

Return an iterable of all empty positions within radius `r` from the given position or the given agent.

The value of `r` and possible keywords operate identically to [`nearby_positions`](@ref).
