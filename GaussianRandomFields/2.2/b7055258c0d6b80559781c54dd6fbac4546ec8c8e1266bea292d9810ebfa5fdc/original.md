```
Matern(λ, ν, [σ = 1], [p = 2])
```

Matérn covariance structure with correlation length `λ`, smoothness `ν`, (optional) marginal standard deviation `σ` and (optional) `p`-norm, defined as

$C(x, y) = σ^2 \displaystyle\frac{2^{1 - ν}}{Γ(ν)} \left(\frac{ρ}{λ}\right)^ν K_ν\left(\frac{ρ}{λ}\right)$

with $ρ = ||x - y||_p$.

# Examples

```jldoctest
julia> Matern(0.1, 1.0)
Matérn (λ=0.1, ν=1.0, σ=1.0, p=2.0)

julia> Matern(1, 1, σ=2.0)
Matérn (λ=1.0, ν=1.0, σ=2.0, p=2.0)

```

See also: [`Exponential`](@ref), [`Linear`](@ref), [`Spherical`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref)
