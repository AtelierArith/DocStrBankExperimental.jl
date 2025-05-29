```
add_flow_vertex!(::Client, mg, resource::MBQCResourceState)
```

This function adds both forward and backward flow vertices to the meta graph for a client in the MBQC model.  It calls the `add_flow_vertex!` function twice, once with `ForwardFlow` and once with `BackwardFlow`.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to which the properties will be added.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.

# Returns

  * The updated MetaGraph.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
add_flow_vertex!(client, mg, resource)
```
