```
mutable struct DiGraph{T<:Integer} <: ADiGraph
    ne::Int
    fadjlist::Vector{Vector{T}}
    badjlist::Vector{Vector{T}}
end
```

A simple digraph type based on two adjacency lists (forward and backward).

```
DiGraph{T}(n=0)
DiGraph(n=0) = DiGraph{Int}(n)
```

Construct a `DiGraph` with `n` vertices and no edges.

```
DiGraph{T}(adjmx::AbstractMatrix; selfedges=true)
```

Construct a `DiGraph{T}` from the adjacency matrix `adjmx`, placing an edge in correspondence to each nonzero element of `adjmx`. If `selfedges=false` the diagonal elements of `adjmx` are ignored.
