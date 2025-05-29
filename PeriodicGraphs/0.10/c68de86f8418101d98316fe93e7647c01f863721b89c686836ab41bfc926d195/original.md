```
normalize_cycle!(cycle::Vector{Int}, n, v::Val{D}) where D
```

In-place rotate and possibly reverse `cycle`, a `Vector{Int}` whose elements are the `hash_position` of vertices of `g` so that the result is the same for all such vectors that represent the same cycle, possibly translated to a different unit cell or rotated.

The graph `g::PeriodicGraph{D}` is represented as `n = nv(g)` and `v = Val(D)`
