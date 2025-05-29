```
eKinetics(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                    AbstractVector{<:AbstractGTBasisFuncs{T, D}}}) where {T, D} -> 
Matrix{T}
```

基底セットに基づいて電子運動エネルギー行列を返します。
