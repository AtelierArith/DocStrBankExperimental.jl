```
normalizeBasis(b::BasisFuncs{T, D}) where {T, D} -> Vector{<:FloatingGTBasisFuncs{T, D}}
```

`b`の各[`BasisFunc`](@ref)を正規化し、それらを1つの[`BasisFuncs`](@ref)にマージしようとします。すべての`BasisFunc`がマージできる場合、返される結果は1要素の`Vector`になります。
