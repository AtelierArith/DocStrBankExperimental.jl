```
construct(ys::T, Xs::T) where {T<:Tuple{NamedMatrix,NamedMatrix}}
```

Construct the query-feature-source-target network for *de novo* network-based inference prediction and return adjacency matrix.

# Arguments

  * `dts::Tuple{NamedMatrix,NamedMatrix}` : Source-target bipartite graph adjacency matrices
  * `dfs::Tuple{NamedMatrix,NamedMatrix}` : Source-feature bipartite graph adjacency matrices

# Extended help

This implementations is intended for time-split cross-validation or manual construction of query network.
