```
sources(N::AbstractNode)
```

A vector of all sources referenced by calls `N()` and `fit!(N)`. These are the sources of the ancestor graph of `N` when including training edges.

Not to be confused with `origins(N)`, in which training edges are excluded.

See also: [`origins`](@ref), [`source`](@ref).
