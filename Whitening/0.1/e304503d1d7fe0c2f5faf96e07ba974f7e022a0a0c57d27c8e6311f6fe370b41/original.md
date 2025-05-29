```
whiten(K::AbstractWhiteningTransform{T}, X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

Transform the rows of `X` to whitened vectors, i.e. `Z = (X .- μᵀ) * Wᵀ`, using the provided kernel. That is, `X` is an `m × n` matrix and `K` is a transformation kernel whose input dimension is `n`.

If `K` compresses `n ↦ p`, i.e. `z = Wx : ℝⁿ ↦ ℝᵖ`, then `Z` is an `m × p` matrix.
