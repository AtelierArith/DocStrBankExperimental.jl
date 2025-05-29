```
fit(x, y, deg=length(x) - 1; [weights], var=:x)
fit(::Type{<:AbstractPolynomial}, x, y, deg=length(x)-1; [weights], var=:x)
```

Fit the given data as a polynomial type with the given degree. Uses linear least squares to minimize the norm  `||y - V⋅β||^2`, where `V` is the Vandermonde matrix and `β` are the coefficients of the polynomial fit.

This will automatically scale your data to the [`domain`](@ref) of the polynomial type using [`mapdomain`](@ref). The default polynomial type is [`Polynomial`](@ref).

## Weights

Weights may be assigned to the points by specifying a vector or matrix of weights.

When specified as a vector, `[w₁,…,wₙ]`, the weights should be non-negative as the minimization problem is `argmin_β Σᵢ wᵢ |yᵢ - Σⱼ Vᵢⱼ βⱼ|² = argmin_β || √(W)⋅(y - V(x)β)||²`, where, `W` the diagonal matrix formed from `[w₁,…,wₙ]`, is used for the solution, `V` being the Vandermonde matrix of `x` corresponding to the specified degree. This parameterization of the weights is different from that of `numpy.polyfit`, where the weights would be specified through `[ω₁,ω₂,…,ωₙ] = [√w₁, √w₂,…,√wₙ]` with the answer solving `argminᵦ | (ωᵢ⋅yᵢ- ΣⱼVᵢⱼ(ω⋅x) βⱼ) |^2`.

When specified as a matrix, `W`, the solution is through the normal equations `(VᵀWV)β = (Vᵀy)`, again `V` being the Vandermonde matrix of `x` corresponding to the specified degree.

(In statistics, the vector case corresponds to weighted least squares, where weights are typically given by `wᵢ = 1/σᵢ²`, the `σᵢ²` being the variance of the measurement; the matrix specification follows that of the generalized least squares estimator with `W = Σ⁻¹`, the inverse of the variance-covariance matrix.)

## large degree

For fitting with a large degree, the Vandermonde matrix is exponentially ill-conditioned. The `ArnoldiFit` type introduces an Arnoldi orthogonalization that fixes this problem.
