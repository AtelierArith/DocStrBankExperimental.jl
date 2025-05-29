```
add_edges!(sim, to::AgentID, edges)
```

Add multiple `edges` at once to the simulation `sim`, with all edges are directed to `to`.

`edges` can be any iterable set of agents, or an arbitrary number of edges as arguments. 

See also [`Edge`](@ref) [`register_edgetype!`](@ref) and [`add_edge!`](@ref)
