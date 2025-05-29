```
UniIndepMCSampling <: AbstractUnivariateMethod
```

An integral evaluation method that uses uniform Monte Carlo sampling to approximate the integral similar to [`UniMCSampling`](@ref MeasureToolbox.UniMCSampling). However, this variant will generate its own set of supports and ignore all other supports with the `MCSample` label. Note this is valid only for finite integral domains. This is not compatible with individual dependent parameters. Contains no fields.
