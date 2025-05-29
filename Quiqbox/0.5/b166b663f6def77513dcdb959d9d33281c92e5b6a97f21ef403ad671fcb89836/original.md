```
absorbNormFactor(b::BasisFunc{T, 3, 𝑙, GN, PT}) where {T, 𝑙, GN, PT} -> 
FloatingGTBasisFuncs{T, 3, 𝑙, GN, PT}

absorbNormFactor(b::BasisFuncs{T, 3, 𝑙, GN, PT}) where {T, 𝑙, GN, PT} -> 
Vector{<:FloatingGTBasisFuncs{T, 3, 𝑙, GN, PT}}
```

If `hasNormFactor(`b`) == true`, absorb the normalization factor of each Gaussian-type  orbital inside `b` into the orbital's corresponding contraction coefficient and then set  `.normalizeGTO` of `b` to `false`. Otherwise, directly return `b` when it's a `BasisFunc`,  or `[b]` when it's a `BasisFuncs`.
