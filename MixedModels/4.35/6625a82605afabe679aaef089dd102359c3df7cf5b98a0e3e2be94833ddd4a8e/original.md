```
varest(m::GeneralizedLinearMixedModel)
```

Returns the estimate of ϕ², the variance of the conditional distribution of Y given B.

For models with a dispersion parameter ϕ, this is simply ϕ². For models without a dispersion parameter, this value is `missing`. This differs from `disperion`, which returns `1` for models without a dispersion parameter.

For Gaussian models, this parameter is often called σ².
