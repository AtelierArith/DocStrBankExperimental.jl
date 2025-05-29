```
AnisotropicExponential(A, [σ = 1])
```

Anisotropic exponential covariance structure with anisotropy matrix `A` and (optional) marginal standard deviation `σ`, defined as

$C(x, y) = \exp(-ρᵀ A ρ)$

where $ρ = x - y$.

# Examples

```jldoctest
julia> A = [1 0.5; 0.5 1];

julia> AnisotropicExponential(A)
anisotropic exponential (A=[1.0 0.5; 0.5 1.0], σ=1.0)

```
