```julia
struct Tuple{T<:Integer, T<:Integer}
```

A `NestedVertex` is the local view of a vertex inside a `NestedGraph`. It contains the subgraph and the vertex indices. Basically, it's an alias for a 2-element Tuple.
