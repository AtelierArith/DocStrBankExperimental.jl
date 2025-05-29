```
whiten(K::AbstractWhiteningTransform{T}, x::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

Transform `x` to a whitened vector, i.e. `z = W * (x - μ)`, using the transformation kernel, `K`.

If `K` compresses `n ↦ p`, then `z ∈ ℝᵖ`.
