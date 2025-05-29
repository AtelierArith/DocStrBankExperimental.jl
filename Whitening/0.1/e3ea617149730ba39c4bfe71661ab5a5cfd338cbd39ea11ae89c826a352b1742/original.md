```
GeneralizedPCA(μ::AbstractVector{T}, Σ::AbstractMatrix{T};
               num_components::Union{Int, Nothing}=nothing,
               vmin::Union{T, Nothing}=nothing,
               rtol::Union{T, Nothing}=nothing) where {T<:Base.IEEEFloat}
```

Construct a generalized PCA transformer from the mean vector, `μ` ∈ ℝⁿ, and a covariance matrix, `Σ` ∈ ℝⁿˣⁿ; `Σ` must be symmetric and positive semi-definite.

The output dimension, `m`, of the transformer is determined from the optional arguments, where

1. 0 ≤ `num_components` ≤ n is a pre-determined size
2. 0 ≤ `vmin` ≤ 1 is the fraction of the total squared cross-covariance,  hence, `m` is the smallest value such that `sum(λ[1:m]) ≥ vmin*sum(λ)`,  where $λᵢ, i=1,…,n$ are the eigenvalues of `Σ` in descending order.
3. `rtol` is the relative tolerance on the number of eigenvalues greater than `rtol*λ₁` where `λ₁` is the largest eigenvalue of `Σ`.

If none of the 3 options are provided, the default is `rtol = n*eps(T)`. If 2 or more options are provided, the minimum of the resultant sizes will be chosen.
