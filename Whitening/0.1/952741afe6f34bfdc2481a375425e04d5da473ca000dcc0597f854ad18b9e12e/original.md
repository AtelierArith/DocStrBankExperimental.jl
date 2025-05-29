```
mahalanobis(K::AbstractWhiteningTransform{T}, x::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

Return the Mahalanobis distance, `√((x - μ)' * Σ⁻¹ * (x - μ))`, computed using the transformation kernel, `K`.
