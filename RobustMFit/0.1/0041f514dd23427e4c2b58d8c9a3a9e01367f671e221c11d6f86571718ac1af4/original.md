```
RAE(d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
RAE(d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
RAE(x::Vector{Real}, d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
RAE(x::Vector{Real}, d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
```

Relative asymptotic efficiency of M-estimator compared to Maximum Likelihood estimation. Computation is based on [`AVar`](@ref AVar) and [`FInfo`](@ref FInfo).

If the distribution `d` has multiple parameters, the keyword argument `single` can be set to `single = true` (default) if single variances shall be compared. `single = false' computes the p-th root of det(Σ₁)/det(Σ₂) where Σ₁ is the covariance matrix of an ML-estimator and Σ₂ the covariance matrix of the M-estimator.

# Example

```julia
d = Poisson(10)
x = rand(d, 200)
spec = Huber(1.5)
λ = Mfit(x, d, spec)
dFit = Poisson(λ)

RAE(dFit, spec, :L)
RAE(x, dFit, spec, :L)

d = Normal(0, 1)
x = rand(d, 200)
spec = [Huber(1.5), Huber(2.5)]
ests = Mfit(x, d, spec)
dFit = NewDist(d, ests)

RAE(dFit, spec, :L, n = 500)
RAE(dFit, spec, :L, n = 500, single = false)
RAE(x, dFit, spec, :L)
```

See [`AVar`](@ref AVar) for additional explanation of arguments.
