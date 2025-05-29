```
set_io_qubits_type!(::Client, resource, mg)
```

This function sets the input/output qubits type property in a MetaGraph based on the round type property of the MetaGraph. 

# Arguments

  * `client::Client`: The Client object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex io type property will be added.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
set_io_qubits_type!(client, resource, mg)
```
