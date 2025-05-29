```
construct(ytrain::T, ytest::T, Xtrain::T, Xtest::T) where {T<:NamedMatrix}
```

Construct the query-feature-source-target network for *de novo* network-based inference prediction and return adjacency matrix.

# Arguments

  * `ytrain::NamedMatrix` : Training source-target bipartite graph adjacency matrix
  * `ytest::NamedMatrix` : Test source-target bipartite graph adjacency matrix
  * `Xtrain::NamedMatrix` : Training source-feature bipartite graph adjacency matrix
  * `Xtest::NamedMatrix` : Test source-feature bipartite graph adjacency matrix

# Extended help

This implementations is intended for time-split cross-validation or manual construction of query network.
