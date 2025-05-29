```
DiNetwork
```

A type representing a directed graph with indexed edges and the possibility to store  graph/vertex/edge properties.

```
DiNetwork(n=0)
```

Construct a `DiNetwork` with `n` vertices and no edges.

```
DiNetwork(adjmx::AbstractMatrix; selfedges=true)
```

Construct a `DiNetwork` from the adjacency matrix `adjmx`. If `selfedges=false` the diagonal elements of `adjmx` are ignored.
