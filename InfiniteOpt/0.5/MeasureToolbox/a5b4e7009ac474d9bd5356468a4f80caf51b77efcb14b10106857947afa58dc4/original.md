```
MultiMCSampling <: AbstractMultivariateMethod
```

An integral evaluation method that uses uniform Monte Carlo sampling to approximate the integral. This variant will add more supports to the model as needed to satisfy `num_supports` and it will include all supports with the `MCSample` label up till the integral is expanded and/or when the infinite model is optimized, whichever comes first. Note this is valid only for finite integral domains. If an array of independent infinite parameters is specified, they must use the same amount of supports. Contains no fields.
