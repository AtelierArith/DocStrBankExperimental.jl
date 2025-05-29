```
num_edges(sim, id::AgentID, ::Type{E})
```

Returns the number of edges of type `E` with agent `id` as target.

`num_edges` is not defined if T has the hint :SingleEdge

See also [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`edgestates`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
