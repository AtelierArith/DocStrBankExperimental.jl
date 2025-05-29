```
add_correction_vertices!(::Client, mg, resource::MBQCResourceState)
```

This function adds correction vertices to the meta graph for a client in the MBQC model.  It iterates over each vertex in the resource, gets the correction vertices for each,  and sets these as properties in the meta graph.

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
add_correction_vertices!(client, mg, resource)
```
