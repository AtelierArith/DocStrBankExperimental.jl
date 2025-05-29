```
add_edge!(sim, to::AgentID, edge::Edge{T})
```

Add a single edge to the simulation `sim`. The edges is directed from the agent with ID `edge.from` (the source) to the agent with ID `to` (the target).

```
add_edge!(sim, from::AgentID, to::AgentID, state::T)
```

Add a single edge to the simulation `sim`. The edge is directed from the agent with ID `from` (the source) to the agent with ID `to` (the target) and has the state `state`.

`T` must have been previously registered in the simulation by calling [`register_edgetype!`](@ref).

See also [`Edge`](@ref) [`register_edgetype!`](@ref) and [`add_edges!`](@ref)
