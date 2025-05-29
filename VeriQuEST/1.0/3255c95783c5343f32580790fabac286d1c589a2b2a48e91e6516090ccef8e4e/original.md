```
set_vertex_type!(::Union{MBQC,ComputationRound}, resource, mg)
```

This function sets the vertex type property in a MetaGraph based on the color pattern of the computation round in the resource graph.  It assigns the `ComputationQubit` type to the vertices according to the color pattern.

# Arguments

  * `mbqc::Union{MBQC,ComputationRound}`: The MBQC or ComputationRound object.
  * `resource`: The resource containing the graph and its coloring.
  * `mg`: The MetaGraph to which the vertex type property will be added.

# Examples

```julia
mbqc = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_vertex_type!(mbqc, resource, mg)
```
