```
construct(y::NamedMatrix, X::NamedMatrix, queries::AbstractVector)
```

Construct the query-feature-source-target network for *de novo* network-based inference prediction and return adjacency matrix.

# Arguments

  * `y::NamedMatrix`: Source-target bipartite network adjacency matrix
  * `X::NamedMatrix`: Source-feature bipartite adjacency matrix
  * `queries::AbstractVector`: Source nodes to use as query

# Extended help

This implementation is intended for k-fold or leave-one-out cross-validation.
