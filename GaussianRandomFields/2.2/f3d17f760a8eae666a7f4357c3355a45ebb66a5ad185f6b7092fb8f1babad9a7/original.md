```
Whittle(λ, [σ = 1], [p = 2])
```

Whittle covariance structure with correlation length `λ`, (optional) marginal standard deviation `σ` and (optional) `p`-norm, defined as

$C(x, y) = σ^2 \displaystyle\frac{ρ}{λ} K₁\left(\frac{ρ}{λ}\right)$

with $ρ = ||x-y||_p$.

# Examples

```jldoctest
julia> Whittle(0.1)
Whittle (λ=0.1, σ=1.0, p=2.0)

julia> Whittle(1.0, σ=2)
Whittle (λ=1.0, σ=2.0, p=2.0)

```

See also: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
