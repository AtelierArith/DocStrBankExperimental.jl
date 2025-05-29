```
normalizeBasis(b::BasisFuncs{T, D}) where {T, D} -> Vector{<:FloatingGTBasisFuncs{T, D}}
```

Normalize each [`BasisFunc`](@ref) inside `b` and try to merge them back to one  [`BasisFuncs`](@ref). If the all the `BasisFunc`(s) can be merged, the returned result will  be a 1-element `Vector`.
