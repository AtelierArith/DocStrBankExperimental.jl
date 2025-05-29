```
absorbNormFactor(bs::AbstractVector{<:GTBasisFuncs{T, 3}}) where {T} -> 
AbstractVector{<:GTBasisFuncs{T, 3}}

absorbNormFactor(bs::Tuple{Vararg{GTBasisFuncs{T, 3}}}) where {T} -> 
Tuple{Vararg{GTBasisFuncs{T, 3}}}
```

`bs`のすべての要素に`absorbNormFactor`を適用します。
