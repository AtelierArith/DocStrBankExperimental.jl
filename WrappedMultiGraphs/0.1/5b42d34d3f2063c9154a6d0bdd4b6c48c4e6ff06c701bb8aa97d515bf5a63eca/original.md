```julia
struct SingleMultiEdge{T<:Integer} <: Graphs.SimpleGraphs.AbstractSimpleEdge{T<:Integer}
```

  * `src::Integer`: The source node
  * `dst::Integer`: The destination node
  * `m::Integer`: The multiplicity of the edge

The `m`-th instance of an edge connecting `src` and `dst`.
