```
add_graph!(sim::Simulation, graph, agent_constructor, edge_constructor) -> Vector{AgentID}
```

Adds a `graph` from the Graphs.jl package to `sim`, incl. all vertices of `graph` as new agents.

`graph` must be a Graphs.Graph or a Graphs.DiGraph.

For each vertix of `graph` the `agent_constructor` function is called, with the Graphs.vertix as argument. For each edge of `graph` the `edge_constructor` function is called, with the Graphs.edge as argument.

The agent types of agents created by the `agent_constructor` must be already registered via [`register_agenttype!`](@ref) and vis a vis the edge type via [`register_edgetype!`](@ref).

!!! info
    add_graph! is only available when the Graphs.jl package is imported by the model implementation.


Returns a vector with the IDs of the created agents.
