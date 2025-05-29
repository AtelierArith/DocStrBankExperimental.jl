```
Network
```

A type representing a graph with indexed edges and the possibility to store  graph/vertex/edge properties.

```
Network(n=0)
```

Construct a `Network` with `n` vertices and no edges.

```
Network(adjmx::AbstractMatrix; selfedges=true, upper=false)
```

Construct a `Network` from the adjacency matrix `adjmx`, placing an edge in correspondence to each nonzero element of `adjmx`. If `selfedges=false` the diagonal elements of `adjmx` are ignored. If `upper=true` only the upper triangular part of `adjmx` is considered.
