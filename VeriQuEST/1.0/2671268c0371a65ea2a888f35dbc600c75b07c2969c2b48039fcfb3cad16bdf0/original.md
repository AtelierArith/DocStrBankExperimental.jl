```
set_io_qubits_type!(::MBQC, resource, mg)
```

This function sets the input/output qubits type property in a MetaGraph for MBQC with no blind.  It assigns the `InputQubits` type to the vertices that are in the input indices and `NoInputQubits` to the rest.

# Arguments

  * `client::MBQC`: The MBQC client object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex io type property will be added.

# Examples

```julia
client = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(client, resource, mg)
```
