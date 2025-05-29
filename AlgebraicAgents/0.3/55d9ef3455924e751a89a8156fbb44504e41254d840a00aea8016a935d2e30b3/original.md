```
step!(agent, t=projected_to(agent))
```

Performs a single evolutionary step of the hierarchy. To avoid frontrunning, solutions will be projected only up to time `t`. This is a two-phase step; the corresponding stepping functions are `_prestep!` and `step!`.

More particular behavior can be implemented using [`Opera`](@ref) protocol.

For custom agents' types, it suffices to implement [`_step!`](@ref).

# Return values

Return `true` if all internal agent's time horizon was reached. Else return the minimum time up to which the agent's solution was projected.
