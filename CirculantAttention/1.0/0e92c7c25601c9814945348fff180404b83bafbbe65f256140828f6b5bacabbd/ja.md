```
y = circulant_attention(A::Circulant, x::AbstractArray)
y = A ⊗ x # \otimes
```

循環行列 `A` を `x` に適用します。詳細は [`circulant_adjacency`](@ref) を参照してください。
