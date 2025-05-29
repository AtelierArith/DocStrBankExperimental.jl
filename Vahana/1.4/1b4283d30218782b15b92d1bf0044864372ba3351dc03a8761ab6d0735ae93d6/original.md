```
edges(sim, id::AgentID, ::Type{E})
```

Returns the edge of type `E` with agent `id` as target if `E` has the hint :SingleEdge, or a vector of these edges otherwise.

If there is no edge with agent `id` as target, `edges` returns `nothing`.

edges is not defined if `E` has the hint :IgnoreFrom or :Stateless.

See also [`apply!`](@ref), [`neighborids`](@ref), [`edgestates`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) and [`neighborstates`](@ref)
