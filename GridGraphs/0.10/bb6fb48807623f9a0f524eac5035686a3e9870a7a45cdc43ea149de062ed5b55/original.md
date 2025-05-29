```
ShortestPathTree{R<:Real}
```

Storage for the result of a single-source shortest paths query with source `s`.

# Fields

  * `parents::Vector{Int}`: the parent of each vertex `v` in a shortest `s -> v` path.
  * `dists::Vector{R}`: the distance of each vertex `v` from `s`.
