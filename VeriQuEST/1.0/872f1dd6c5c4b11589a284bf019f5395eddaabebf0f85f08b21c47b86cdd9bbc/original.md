```
set_io_qubits_type!(::TestRound, resource, mg)
```

In Test rounds there is no classical input, but this holder function allows for unilateral call, regardless of round.  It assigns the `NoInputQubits` type to all the vertices.

# Arguments

  * `round::TestRound`: The TestRound object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex io type property will be added.

# Examples

```julia
round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(round, resource, mg)
```
