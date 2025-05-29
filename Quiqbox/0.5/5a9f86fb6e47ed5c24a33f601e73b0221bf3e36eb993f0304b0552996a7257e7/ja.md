```
sortBasis(b::GTBasis{T, D}; roundAtol::Real=getAtolVal(T)) where {T, D} -> 
GTBasis{T, D}
```

入力の `GTBasis` に格納されている `GTBasisFuncs` をソートして [`GTBasis`](@ref) を再構築します。
