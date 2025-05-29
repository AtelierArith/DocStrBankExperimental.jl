```
mutable struct Graph{T<:Integer} <: AGraph
    ne::Int
    fadjlist::Vector{Vector{T}}
end
```

A simple graph type based on an adjacency list.

The constructors

```
Graph{T}(n=0)
Graph(n=0) = Graph{Int}(n)
```

return a `Graph` with `n` vertices and no edges.

```
Graph{T}(adjmx::AbstractMatrix; upper=false, selfedges=true)
```

Construct a `Graph{T}` from the adjacency matrix `adjmx`, placing an edge in correspondence to each nonzero element of `adjmx`. If `selfedges=false` the diagonal elements of `adjmx` are ignored. If `upper=true` only the upper triangular part of `adjmx` is considered.
