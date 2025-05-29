```
set_io_qubits_type!(::ComputationRound, resource, mg)
```

In Computation round, there are sometimes input values for qubits. When this happens, this function will allocate space for them in the property graph.  It assigns the `InputQubits` type to the vertices that are in the input indices and `NoInputQubits` to the rest.

# Arguments

  * `round::ComputationRound`: The ComputationRound object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex io type property will be added.

# Examples

```julia
round = ComputationRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(round, resource, mg)
```
