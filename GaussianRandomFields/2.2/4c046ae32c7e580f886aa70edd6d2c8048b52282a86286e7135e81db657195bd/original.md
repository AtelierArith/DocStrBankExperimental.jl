```
SeparableCovarianceFunction(cov...)
```

Separable covariance function in `length(cov)` dimensions for the covariance structures `cov`. Usefull for defining anisotropic covariance functions, or if the non-seperable `KarhunenLoeve` expansion is too expensive.

# Examples

```
julia> SeparableCovarianceFunction(Exponential(0.1), Matern(0.01, 1.0))
2d separable covariance function [ exponential (λ=0.1, σ=1.0, p=2.0), Matérn (λ=0.01, ν=1.0, σ=1.0, p=2.0) ]

```

See also: [`CovarianceFunction`](@ref), [`KarhunenLoeve`](@ref)
