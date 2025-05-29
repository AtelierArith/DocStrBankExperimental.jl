```
init_qubit_meta_graph!(::Client, resource, mg)
```

This function initializes the qubit meta graph for a client in the MBQC model.  It retrieves the round type from the meta graph and then calls the appropriate  `init_qubit_meta_graph!` function based on the round type.

# Arguments

  * `::Client`: The Client object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the properties will be added.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
init_qubit_meta_graph!(client, resource, mg)
```
