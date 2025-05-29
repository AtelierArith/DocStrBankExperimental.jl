```
add_flow_vertex!(::Client, mg, resource::MBQCResourceState, flow_type::Union{ForwardFlow,BackwardFlow})
```

This function adds a flow vertex to the meta graph for a client in the MBQC model.  It first converts the flow type to a symbol, then iterates over each vertex in the resource.  For each vertex, it gets the verified flow output and sets this as a property in the meta graph.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to which the properties will be added.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.
  * `flow_type::Union{ForwardFlow,BackwardFlow}`: The flow type to be added.

# Returns

  * The updated MetaGraph.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
flow_type = ForwardFlow()
add_flow_vertex!(client, mg, resource, flow_type)
```
