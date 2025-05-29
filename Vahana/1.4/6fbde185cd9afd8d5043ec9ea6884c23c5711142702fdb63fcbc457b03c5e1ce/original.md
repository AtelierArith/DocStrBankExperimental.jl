```
all_edges(sim, ::Type{T}, [all_ranks=true])
```

This function retrieves a vector of (AgentID, Edge) tuples for all edges of type T of the simulation `sim`.

The AgentID in the tuple is the target of the edge. The specific form of the edge in the tuple depends on the hints for type T.

The `all_ranks` argument determines whether to include edges from all ranks or just the current rank in parallel simulations. When `all_ranks` is `true`, the function returns a vector of all edges identifiers across all ranks.  

See also [`add_edge!`](@ref) and [`num_edges`](@ref).
