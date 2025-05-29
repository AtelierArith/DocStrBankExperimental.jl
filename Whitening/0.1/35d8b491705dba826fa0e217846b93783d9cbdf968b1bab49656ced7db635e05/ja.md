```
unwhiten(K::AbstractWhiteningTransform{T}, z::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

`z`を、カーネル`K`に属する非ホワイト化ベクトルの元の座標系に変換します。すなわち、`x = μ + W⁻¹ * z`です。これは`whiten(K, x)`の逆です。

もし`K`が`n ↦ p`を圧縮するなら、`x ∈ ℝⁿ`です。
