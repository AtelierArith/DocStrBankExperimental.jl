```
Spherical(λ, [σ = 1], [p = 2])
```

Spherical covariance structure with correlation length `λ`, (optional) marginal standard deviation `σ` and (optional) `p`-norm, defined as

$C(x, y) = \begin{cases} σ^2 \left(1 - \displaystyle\frac{3}{2}\frac{ρ}{λ} + \frac{1}{2}\left(\frac{ρ}{λ}\right)^3\right) & \text{for }ρ≤λ\\0 & \text{for }ρ>λ\end{cases}$

with $ρ = ||x - y||_p$.

# Examples

```jldoctest
julia> Spherical(0.1)
spherical (λ=0.1, σ=1.0, p=2.0)

julia> Spherical(1.0, σ=2)
spherical (λ=1.0, σ=2.0, p=2.0)

```

See also: [`Exponential`](@ref), [`Linear`](@ref), [`Whittle`](@ref), [`Gaussian`](@ref), [`SquaredExponential`](@ref), [`Matern`](@ref)
