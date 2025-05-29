```julia
struct NestedGraph{T<:Integer, R<:Graphs.AbstractGraph{T<:Integer}, N<:Graphs.AbstractGraph} <: Graphs.AbstractGraph{T<:Integer}
```

  * `flatgr::Graphs.AbstractGraph{T} where T<:Integer`: Flat graph view combining all subgraph graphs given with the edges
  * `grv::Vector{N} where N<:Graphs.AbstractGraph`: Original subgraph graphs
  * `neds::Array{NestedGraphs.NestedEdge{T}, 1} where T<:Integer`: intersubgraph edges
  * `vmap::Array{Tuple{T, T}, 1} where T<:Integer`: Maps the nodes of flat network to the original graph (Subgraph, Node)

A `NestedGraph` is a graph of vertices, where each vertex can be a complete graph. Connections are done with `NestedEdge`s and the vertices are `NestedVertex`s. NestedGraphs of NestedGraphs are allowed.
