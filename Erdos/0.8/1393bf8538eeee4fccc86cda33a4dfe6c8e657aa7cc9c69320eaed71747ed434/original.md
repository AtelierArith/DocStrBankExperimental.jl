```
nonbacktrack_embedding(g::AGraph, k::Int)
```

Spectral embedding of the non-backtracking matrix of `g` (see [Krzakala et al.](http://www.pnas.org/content/110/52/20935.short)).

```
`g`: imput Graph
`k`: number of dimensions in which to embed
```

Returns  a matrix `ϕ` where `ϕ[:,i]` are the coordinates for vertex `i`.

Note:  does not explicitly construct the [`nonbacktracking_matrix`](@ref). See [`nonbacktracking_matrix`](@ref) for details.
