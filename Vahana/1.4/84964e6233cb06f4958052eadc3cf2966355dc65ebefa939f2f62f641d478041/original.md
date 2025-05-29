```
neighborstates_flexible(sim::Simulation, id::AgentID, ::Type{E})
```

Returns the state of the agent on the source of the edge of type `E` with agent `id` as target if `E` has the hint :SingleEdge, or a vector of these agent states otherwise.

If there is no edge with agent `id` as target, `neighborstates_flexible` returns `nothing`.

`neighborstates_flexible` is the type instable version of [`neighborstates`](@ref) and should be only used in the case that the type of agent can not be determined.

`neighborstates_flexible` is not defined if T has the hint :IgnoreFrom.

!!! tip
    If the edge type `E` does not have the :SingleEdge hint, `neighborstates_flexible` allocates memory for the vector of  agent states. To avoid this allocation, you can use `neighborstates_flexible_iter` instead.


See also [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`edgestates`](@ref)
