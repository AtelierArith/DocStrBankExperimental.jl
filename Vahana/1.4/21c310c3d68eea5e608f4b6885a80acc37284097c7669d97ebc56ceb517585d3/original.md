```
neighborstates_iter(sim::Simulation, id::AgentID, ::Type{E}, ::Type{A})
```

Returns an iterator for the states of the agents with type `A`  on the source of the edges  of type `E` with agent `id` as target.

If there is no edge with agent `id` as target, the function returns `nothing`.

When the agents on the source side of the edges can have different types, and it is impossible to determine the Type{A} you can use [`neighborstates_flexible_iter`](@ref) instead.

`neighborstates_iter` is not defined if T has the hint :IgnoreFrom or :SingleEdge.

See also [`neighborstates`](@ref), [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`edgestates`](@ref) 
