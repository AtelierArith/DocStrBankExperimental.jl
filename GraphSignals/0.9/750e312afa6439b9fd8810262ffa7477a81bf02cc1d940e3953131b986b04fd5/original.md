```
aggregate_index(sg; direction=:undirected, kind=:edge)
```

Generate index structure for scatter operation.

# Arguments

  * `sg::SparseGraph`: The reference graph.
  * `direction::Symbol`: The direction of an edge to be choose to aggregate. It must be one of `:inward` and `:outward`.
  * `kind::Symbol`: To aggregate feature upon edge or vertex. It must be one of `:edge` and `:vertex`.
