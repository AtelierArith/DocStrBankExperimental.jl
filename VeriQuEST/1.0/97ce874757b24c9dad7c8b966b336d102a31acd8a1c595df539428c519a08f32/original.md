```
entangle_graph!(::Client, mg)
```

This function entangles the quantum state of a meta graph for a client in the MBQC model.  It first retrieves the quantum state from the meta graph and creates a graph from the meta graph.  Then, for each edge in the graph, it applies a controlled phase flip operation on the source and destination vertices.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to which the properties will be added.

# Examples

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
entangle_graph!(client, mg)
```
