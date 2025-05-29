```
SquaredExponential(λ, [σ = 1], [p = 2])
```

Squared exponential (Gaussian) covariance structure with correlation length `λ`, (optional) marginal standard deviation `σ` and (optional) `p`-norm, defined as

$C(x, y) = σ^2 \exp\left(-\left(\displaystyle\frac{ρ}{λ}\right)^2\right)$

with $ρ = ||x - y||_p$.

# Examples

```jldoctest
julia> SquaredExponential(0.1)
Gaussian (λ=0.1, σ=1.0, p=2.0)

julia> SquaredExponential(1, σ=2.)
Gaussian (λ=1.0, σ=2.0, p=2.0)

```

See also: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`Matern`](@ref)
