```julia
struct UnitDiskGraph{D, T} <: Graphs.AbstractGraph{Int64}
```

A unit disk graph is a graph in which the vertices are points in a plane and two vertices are connected by an edge if and only if the Euclidean distance between them is at most a given radius.

### Fields

  * `locations::Vector{NTuple{D, T}}`: the locations of the vertices
  * `radius::Float64`: the radius of the unit disk
