```
siteinds(uniqueinds, A::MPO, B::MPS)
siteinds(uniqueind, A::MPO, B::MPO)
```

Get the site indices of MPO `A` that are unique to `A` (not shared with MPS/MPO `B`), as a `Vector{<:Index}`.
