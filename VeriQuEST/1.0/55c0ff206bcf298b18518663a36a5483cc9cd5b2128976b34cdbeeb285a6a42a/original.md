```
add_output_qubits!(::Client, mg, resource::MBQCResourceState)
```

This function adds output qubits to the meta graph for a client in the MBQC model.  It retrieves the output indices from the resource graph and sets the `:output_inds` property of the meta graph to these indices.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to which the property will be added.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.

# Returns

  * The updated MetaGraph.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
add_output_qubits!(client, mg, resource)
```
