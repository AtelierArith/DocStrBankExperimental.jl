```
MultiIndepMCSampling <: AbstractMultivariateMethod
```

An integral evaluation method that uses uniform Monte Carlo sampling to approximate the integral similar to [`MultiMCSampling`](@ref MeasureToolbox.MultiMCSampling). However, this variant will generate its own set of supports and ignore all other supports with the `MCSample` label. Note this is valid only for finite integral domains. Contains no fields.
