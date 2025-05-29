```
neighborids(sim, id::AgentID, ::Type{E})
```

Returns the ID of the agent on the source of the edge of type `E` with agent `id` as target if `E` has the hint :SingleEdge, or otherwise a vector of the IDs of the agents on the source side of those edges.

If there is no edge with agent `id` as target, `neighborids` returns `nothing`.

`neighborids` is not defined if `E` has the hint :IgnoreFrom.

!!! tip
    If the edge type `E` does not have the :Stateless or :SingleEdge  hint, `neighborids` allocates memory for the vector of agent ids. To avoid this allocation, you can use `neighborids_iter`  instead.


See also [`apply!`](@ref), [`edges`](@ref), [`edgestates`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
