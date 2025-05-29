```
AVar(d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
AVar(d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
AVar(x::Vector{Real}, d::UnivariateDistribution, spec::MSetting, biasCorr::Union{Symbol, String})
AVar(x::Vector{Real}, d::UnivariateDistribution, spec::Vector{MSetting}, biasCorr::Union{Symbol, String})
```

Asymptotic variance / covariance matrix of M-estimators.

If the fitted distribution `d` has multiple parameters, different specification used in estimation can be provided.

The asymptotic variance / covariance matrix can be computed either for a fitted distribution `d` or  estimated using the sample `c` and the fitted distribution `d`.

The argument `biasCorr` specifies which method was used in the estimation to correct for a potential bias.

If the fitted distribution `d` is continuous and no sample is provided, the computation relies on numerical evaluation of vexpectations using the [Expectations.jl package](https://github.com/QuantEcon/Expectations.jl). The precision of numerical integration is controlled by additional keyword argument `n` with default `n = 1000`.

# Example

```julia
d = Poisson(10)
x = rand(d, 200)
spec = Huber(1.5)
λ = Mfit(x, d, spec)
dFit = Poisson(λ)

AVar(dFit, spec, :L)
AVar(x, dFit, spec, :L)

d = Normal(0, 1)
x = rand(d, 200)
spec = [Huber(1.5), Huber(2.5)]
ests = Mfit(x, d, spec)
dFit = NewDist(d, ests)

AVar(dFit, spec, :L, n = 500)
AVar(x, dFit, spec, :L)
```

See [Stefanski and Book (2002)](https://www.jstor.org/stable/3087324) for theoretical background.
