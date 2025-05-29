```
CovarianceFunction(d, cov)
```

Covariance function in `d` dimensions with covariance structure `cov`.

# Examples

```jldoctest
julia> CovarianceFunction(1, Exponential(0.1))
1d exponential covariance function (λ=0.1, σ=1.0, p=2.0)

julia> CovarianceFunction(2, Matern(0.1, 1.0))
2d Matérn covariance function (λ=0.1, ν=1.0, σ=1.0, p=2.0)

```
