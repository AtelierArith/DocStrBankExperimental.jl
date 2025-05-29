```
sortPermBasis(bs::AbstractArray{<:CompositeGTBasisFuncs{T, D}}; 
              roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector{Int}
```

`bs[I] ==`[`sortBasis`](@ref) `(bs; roundAtol)[I]` のようなインデックス `I` の `Vector` を返します。
