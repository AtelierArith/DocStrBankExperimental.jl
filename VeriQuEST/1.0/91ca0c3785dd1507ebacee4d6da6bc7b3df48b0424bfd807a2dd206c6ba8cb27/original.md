```
init_qubit_meta_graph!(::Client, mbqc::MBQC, resource::MBQCResourceState, mg)
```

This function initializes the qubit meta graph for a client in the MBQC model.  It sets the secret angle and initial qubit properties for each vertex in the meta graph.

# Arguments

  * `client::Client`: The Client object.
  * `mbqc::MBQC`: The MBQC object.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the properties will be added.

# Examples

```julia
client = Client()
mbqc = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, mbqc, resource, mg)
```
