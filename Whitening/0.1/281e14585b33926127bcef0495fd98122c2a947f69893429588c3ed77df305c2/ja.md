```
unwhiten(K::AbstractWhiteningTransform{T}, Z::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

行列 `Z` の行を非ホワイト化されたベクトルに変換します。すなわち、`X = Z * (W⁻¹)ᵀ .+ μᵀ` を使用して、提供されたカーネルを用います。つまり、`Z` は `m × p` 行列であり、`K` は出力次元が `p` の変換カーネルです。

もし `K` が `n ↦ p` を圧縮する場合、すなわち `z = Wx : ℝⁿ ↦ ℝᵖ` であれば、`X` は `m × n` 行列になります。
