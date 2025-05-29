```
mergenodes(
    fens::FENodeSet{T},
    fes::AbstractFESet,
    tolerance::T,
    candidates::AbstractVector{IT},
) where {T<:Number, IT<:Integer}
```

Merge together  nodes of a single node set.

Similar to `mergenodes(fens, fes, tolerance)`, but only the candidate nodes are considered for merging. This can potentially speed up the operation by orders of magnitude.
