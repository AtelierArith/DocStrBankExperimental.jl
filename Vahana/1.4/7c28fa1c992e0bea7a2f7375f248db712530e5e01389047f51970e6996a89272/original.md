```
neighborids_iter(sim, id::AgentID, ::Type{E})
```

Returns an iterator of the IDs of the agents on the source side of edges of type `E` with agent `id` as target.

If there is no edge with agent `id` as target, the function returns `nothing`.

`neighborids` is not defined if `E` has the hint :SingleEdge or :IgnoreFrom.

See also [`apply!`](@ref), [`neighborids`](@ref), [`edges`](@ref), [`edgestates`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
