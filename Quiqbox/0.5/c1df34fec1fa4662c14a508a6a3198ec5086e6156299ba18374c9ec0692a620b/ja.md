```
flatten(bs::AbstractVector{<:GTBasisFuncs{T, D}}) where {T, D} -> 
AbstractVector{<:GTBasisFuncs{T, D, 1}}

flatten(bs::Tuple{Vararg{GTBasisFuncs{T, D}}}) where {T, D} -> 
Tuple{Vararg{GTBasisFuncs{T, D, 1}}}
```

`GTBasisFuncs` のコレクションをフラット化し、すべての `GTBasisFuncs{T, D, ON}` を `ON > 1` の場合に複数の `GTBasisFuncs{T, D, 1}` に分解します。
