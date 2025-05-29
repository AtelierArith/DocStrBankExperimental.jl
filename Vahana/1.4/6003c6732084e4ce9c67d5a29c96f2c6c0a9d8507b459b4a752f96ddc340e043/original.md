```
neighborstates(sim::Simulation, id::AgentID, ::Type{E}, ::Type{A})
```

Returns the state of the agent with type `A` on the source of the edge of type `E` with agent `id` as target if `E` has the hint :SingleEdge, or a vector of these agent states otherwise.

If there is no edge with agent `id` as target, `neighborstates` returns `nothing`.

When the agents on the source side of the edges can have different types, and it is impossible to determine the Type{A} you can use [`neighborstates_flexible`](@ref) instead.

`neighborstates` is not defined if T has the hint :IgnoreFrom 

!!! tip
    If the edge type `E` does not have the :SingleEdge hint, `neighborstates` allocates memory for the vector of agent states. To avoid this allocation, you can use `neighborstates_iter` instead.


See also [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`edgestates`](@ref)
