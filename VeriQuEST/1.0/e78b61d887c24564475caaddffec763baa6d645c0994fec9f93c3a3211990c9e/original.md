```
init_qubit_meta_graph!(::Client, ::TestRound, resource::MBQCResourceState, mg)
```

This function initializes the qubit meta graph for a client in the MBQC model during a test round.  It sets the initial qubit property for each vertex in the meta graph based on the vertex type.

# Arguments

  * `::Client`: The Client object.
  * `::TestRound`: The TestRound object.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the properties will be added.

# Examples

```julia
client = Client()
round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, round, resource, mg)
```
