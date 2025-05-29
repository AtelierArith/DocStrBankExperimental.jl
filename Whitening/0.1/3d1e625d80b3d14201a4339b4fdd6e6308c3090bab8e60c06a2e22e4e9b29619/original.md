```
ZCA(μ::AbstractVector{T}, Σ::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

Construct a ZCA transformer from the from the mean vector, `μ` ∈ ℝⁿ, and a covariance matrix, `Σ` ∈ ℝⁿˣⁿ; `Σ` must be symmetric and positive definite.
