```julia
struct HyperGraph <: Graphs.AbstractGraph{Int64}
```

A hypergraph is a generalization of a graph in which an edge can connect any number of vertices.

### Fields

  * `n::Int`: the number of vertices
  * `edges::Vector{Vector{Int}}`: a vector of vectors of integers, where each vector represents a hyperedge connecting the vertices with the corresponding indices.
