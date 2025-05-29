```
mahalanobis(K::AbstractWhiteningTransform{T}, x::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

変換カーネル `K` を使用して計算されたマハラノビス距離 `√((x - μ)' * Σ⁻¹ * (x - μ))` を返します。
