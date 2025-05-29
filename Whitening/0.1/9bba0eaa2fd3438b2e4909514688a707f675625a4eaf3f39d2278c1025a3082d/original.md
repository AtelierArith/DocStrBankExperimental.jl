```
mahalanobis(K::AbstractWhiteningTransform{T}, X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

Return the Mahalanobis distance, `√((x - μ)' * Σ⁻¹ * (x - μ))`, computed for each row in `X`, using the transformation kernel, `K`.
