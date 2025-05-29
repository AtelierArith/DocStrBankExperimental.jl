```
set_vertex_type!(::TestRound, resource, mg)
```

This function sets the vertex type property in a MetaGraph based on a random color pattern from the test round in the resource graph.  It assigns the `DummyQubit` and `TrapQubit` types to the vertices according to the color pattern.

# Arguments

  * `test_round::TestRound`: The TestRound object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex type property will be added.

# Examples

```julia
test_round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_vertex_type!(test_round, resource, mg)
```
