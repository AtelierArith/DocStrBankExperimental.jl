```
whiten(K::AbstractWhiteningTransform{T}, X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

行列 `X` の行をホワイトニングされたベクトルに変換します。すなわち、`Z = (X .- μᵀ) * Wᵀ` を使用して、提供されたカーネルを用います。つまり、`X` は `m × n` 行列であり、`K` は入力次元が `n` の変換カーネルです。

もし `K` が `n ↦ p` を圧縮する場合、すなわち `z = Wx : ℝⁿ ↦ ℝᵖ` の場合、`Z` は `m × p` 行列になります。
