```
neighborstates_flexible_iter(sim::Simulation, id::AgentID, ::Type{E})
```

Returns an iterator for the states of the agents on the source of the edges  of type `E` with agent `id` as target.

If there is no edge with agent `id` as target, the function returns `nothing`.

`neighborstates_flexible_iter` is the type instable version of [`neighborstates_iter`](@ref) and should be only used in the case that the type of agent can not be determined.

`neighborstates_flexible_iter` is not defined if T has the hint :IgnoreFrom or the hint :SingleEdge.

See also [`neighborstates_flexible`](@ref), [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`edgestates`](@ref)
