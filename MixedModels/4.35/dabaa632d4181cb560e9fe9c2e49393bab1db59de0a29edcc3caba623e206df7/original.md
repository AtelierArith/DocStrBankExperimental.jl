```
sdest(m::GeneralizedLinearMixedModel)
```

Return the estimate of the dispersion, i.e. the standard deviation of the per-observation noise.

For models with a dispersion parameter ϕ, this is simply ϕ. For models without a dispersion parameter, this value is `missing`. This differs from `disperion`, which returns `1` for models without a dispersion parameter.

For Gaussian models, this parameter is often called σ.
