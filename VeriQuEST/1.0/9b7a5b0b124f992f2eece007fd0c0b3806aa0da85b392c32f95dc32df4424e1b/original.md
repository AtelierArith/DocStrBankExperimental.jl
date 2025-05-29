```
init_qubit_meta_graph!(::Client, ::ComputationRound, resource::MBQCResourceState, mg)
```

This function initializes the qubit meta graph for a client in the MBQC model during a computation round.  It sets the secret angle and initial qubit properties for each vertex in the meta graph.

# Arguments

  * `::Client`: The Client object.
  * `::ComputationRound`: The ComputationRound object.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the properties will be added.

# Examples

```julia
client = Client()
round = ComputationRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, round, resource, mg)
```
