```
Linear(λ, [σ = 1], [p = 2])
```

Linear covariance structure with correlation length `λ`, (optional) marginal standard deviation `σ` and (optional) `p`-norm, defined as

$C(x, y) = \begin{cases} σ^2 \left(1 - \displaystyle\frac{ρ}{λ}\right) & \text{if }ρ ≤ λ\\ 0 & \text{if }ρ>λ\end{cases}$

with $ρ = ||x - y||_p$.

# Examples

```jldoctest
julia> Linear(0.1)
linear (λ=0.1, σ=1.0, p=2.0)

julia> Linear(1.0, σ=2)
linear (λ=1.0, σ=2.0, p=2.0)

```

See also: [`Exponential`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
