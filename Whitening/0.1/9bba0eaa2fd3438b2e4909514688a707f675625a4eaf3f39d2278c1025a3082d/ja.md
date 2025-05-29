```
mahalanobis(K::AbstractWhiteningTransform{T}, X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

各行の `X` に対して、変換カーネル `K` を使用して計算されたマハラノビス距離 `√((x - μ)' * Σ⁻¹ * (x - μ))` を返します。
