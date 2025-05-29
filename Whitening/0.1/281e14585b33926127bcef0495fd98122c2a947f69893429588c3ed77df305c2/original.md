```
unwhiten(K::AbstractWhiteningTransform{T}, Z::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

Transform the rows of `Z` to unwhitened vectors, i.e. `X = Z * (W⁻¹)ᵀ .+ μᵀ`, using the provided kernel. That is, `Z` is an `m × p` matrix and `K` is a transformation kernel whose output dimension is `p`.

If `K` compresses `n ↦ p`, i.e. `z = Wx : ℝⁿ ↦ ℝᵖ`, then `X` is an `m × n` matrix.
