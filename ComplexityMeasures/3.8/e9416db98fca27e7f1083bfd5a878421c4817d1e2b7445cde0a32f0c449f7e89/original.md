```
information(est::DifferentialInfoEstimator, x) → h::Real
```

Estimate a **differential information measure** using the provided [`DifferentialInfoEstimator`](@ref) and input data `x`.

## Description

The overwhelming majority of differential estimators estimate the [`Shannon`](@ref) entropy. If the same estimator can estimate different information measures (e.g. it can estimate both [`Shannon`](@ref) and [`Tsallis`](@ref)), then the information measure is provided as an argument to the estimator itself.

See the [table of differential information measure estimators](@ref table_diff_ent_est) in the docs for all differential information measure estimators.

Currently, unlike for the discrete information measures, this method doesn't involve explicitly first computing a probability density function and then passing this density to an information measure definition. But in the future, we want to establish a `density` API similar to the [`probabilities`](@ref) API.

## Examples

To compute the differential version of a measure, give it as the first argument to a [`DifferentialInfoEstimator`](@ref) and pass it to [`information`](@ref).

```julia
x = randn(1000)
h_sh = information(Kraskov(Shannon()), x)
h_vc = information(Vasicek(Shannon()), x)
```

A normal distribution has a base-e Shannon differential entropy of `0.5*log(2π) + 0.5` nats.

```julia
est = Kraskov(k = 5, base = ℯ) # Base `ℯ` for nats.
h = information(est, randn(2_000_000))
abs(h - 0.5*log(2π) - 0.5) # ≈ 0.0001
```
