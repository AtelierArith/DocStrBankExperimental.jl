```
check_valid_symmetry(pge::PeriodicGraphEmbedding{D,T}, t::SVector{D,T}, r=nothing, vtypes=nothing, issorted=false)
```

Check that the periodic graph embedding is identical to that rotated by `r` (if it is not `nothing`) then translated by `t`. If `vtypes` is not `nothing`, any vertex `x` must additionally be mapped to a vertex `y` such that `vtypes[x] == vtypes[y].` If `issorted` is set and `T <: Rational`, assume that `issorted(pge.pos)` to use a faster dichotomy approach.

If so, return the the `vmap` between the initial vertices and their symmetric images, as well as the `offsets` of each symmetric image compared to the origin. Otherwise, return `nothing`.
