```
init_measurement_outcomes!(::Client, mg, resource::MBQCResourceState)
```

This function initializes the measurement outcomes in the meta graph for a client in the MBQC model.  It iterates over each vertex in the resource and sets the `:outcome` property of each vertex in the meta graph to `Int64`.

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
init_measurement_outcomes!(client, mg, resource)
```
