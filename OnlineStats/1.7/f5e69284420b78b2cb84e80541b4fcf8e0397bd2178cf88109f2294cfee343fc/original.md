```
FitCauchy(b=500)
```

Approximate parameter estimation of a Cauchy distribution.  Estimates are based on approximated quantiles.  See [`Quantile`](@ref) and [`ExpandingHist`](@ref) for details on how the distribution is estimated.

# Example

```
o = fit!(FitCauchy(), randn(1000))
```
