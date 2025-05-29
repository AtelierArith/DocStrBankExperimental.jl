```
Factored{N} <: Distribution{Multivariate, MixedSupport}
```

a `Distribution` type that can be used to combine multiple `UnivariateDistribution`'s and sample from them. Example: it can be used as `prior = Factored(Normal(0,1), Uniform(-1,1))`
