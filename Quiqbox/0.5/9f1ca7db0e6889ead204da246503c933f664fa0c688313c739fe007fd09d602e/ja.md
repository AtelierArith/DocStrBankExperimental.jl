```
changeHbasis(b::GTBasis{T, D}, 
             nuc::Tuple{String, Vararg{String, NNMO}}, 
             nucCoords::Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, 
             C::Union{AbstractMatrix{T}, NTuple{2, AbstractMatrix{T}}}) where 
            {T, D, NNMO} -> 
NTuple{2, Any}
```

入力 `C` に基づいて基底の変更後の一体および二体積分を返します。返される `Tuple` の各要素の型は、`changeHbasis` の最初の引数が `AbstractArray` である場合と一致します。
