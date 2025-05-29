```
edgestates_iter(sim, id::AgentID, ::Type{E})
```

Returns an iterator of the states of the edges of type `E` with agent `id` as target.

If there is no edge with agent `id` as target, the function returns `nothing`.

`edgestates_iter` is not defined if `E` has the hint :Stateless or :SingleEdge.

See also [`apply!`](@ref), [`edgestates`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
