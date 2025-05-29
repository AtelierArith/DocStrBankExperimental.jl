```
y = circulant_mh_attention(A::Circulant, x::AbstractArray)
y = A ⨷ x # \Otimes
```

循環行列 `A`（チャネル次元 > 1）を `x` に適用します。詳細は [`circulant_attention`](@ref) および [`circulant_adjacency`](@ref) を参照してください。
