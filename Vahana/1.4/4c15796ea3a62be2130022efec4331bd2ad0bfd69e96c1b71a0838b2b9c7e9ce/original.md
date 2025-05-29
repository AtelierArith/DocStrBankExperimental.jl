```
edgestates(sim, id::AgentID, ::Type{E})
```

Returns the state of the edge of type `E` with agent `id` as target if `E` has the hint :SingleEdge, or a vector of these states otherwise.

If there is no edge with agent `id` as target, `edgestates` returns `nothing`.

`edgestates` is not defined if `E` has the hint :Stateless.

!!! tip
    If the edge type `E` does not have the :Stateless or :SingleEdge hint, `edgestates` allocates memory for the vector of states. To avoid this allocation, you can use `edgestates_iter` instead.


See also [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
