```
unwhiten(K::AbstractWhiteningTransform{T}, z::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

Transform `z` to the original coordinate system of a non-whitened vector belonging to the kernel, `K`, i.e. `x = μ + W⁻¹ * z`. This is the inverse of `whiten(K, x)`.

If `K` compresses `n ↦ p`, then `x ∈ ℝⁿ`.
