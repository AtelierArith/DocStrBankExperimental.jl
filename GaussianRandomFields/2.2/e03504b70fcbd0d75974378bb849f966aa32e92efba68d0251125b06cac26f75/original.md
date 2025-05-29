```
Exponential(λ, [σ = 1], [p = 2])
```

Exponential covariance structure with correlation length `λ`, (optional) marginal standard deviation `σ` and (optional) `p`-norm defined as

$C(x, y) = σ^2 \exp\left(-\displaystyle\frac{ρ}{λ}\right)$

with $ρ = ||x - y||_p$.

# Examples

```jldoctest
julia> Exponential(0.1)
exponential (λ=0.1, σ=1.0, p=2.0)

julia> Exponential(1.0, σ=2)
exponential (λ=1.0, σ=2.0, p=2.0)

```

See also: [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
