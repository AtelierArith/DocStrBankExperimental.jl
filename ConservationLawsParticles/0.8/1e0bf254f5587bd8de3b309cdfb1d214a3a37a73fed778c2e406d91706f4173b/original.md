```
pwc_density(x::AbstractVector)
```

Returns the piecewise constant probability density from the quantile particle positions.

Let the quantile particles be at positions `x₀, x₁, …, xₙ` (remember that in Julia they are actually `x[1], x[2], ..., x[n], x[n+1]`). The returned array `R` is such that `R[1] = R[n+2] = 0` and `R[i] = 1 / (n * (x[i] - x[i-1]))` for the intermediate indices (this formula holds also for the first and last entry if we assume `x[0] = -∞` and `x[n+2] = ∞`).

# Examples

```jldoctest
julia> pwc_density([0, 1, 3])
4-element Vector{Float64}:
 0.0
 0.5
 0.25
 0.0
```
