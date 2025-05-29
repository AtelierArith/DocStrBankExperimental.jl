```
set_vertex_type!(::Client, resource, mg)
```

This function sets the vertex type property in a MetaGraph based on the round type property of the MetaGraph.  It must be implemented after the round type is implemented.

# Arguments

  * `client::Client`: The Client object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex type property will be added.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
set_vertex_type!(client, resource, mg)
```
