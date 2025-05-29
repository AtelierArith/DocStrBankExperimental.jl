```
Product <: MultivariateDistribution
```

An N dimensional `MultivariateDistribution` constructed from a vector of N independent `UnivariateDistribution`s.

```julia
Product(Uniform.(rand(10), 1)) # A 10-dimensional Product from 10 independent `Uniform` distributions.
```

!!! note
    `Product` is deprecated and will be removed in the next breaking release. Use [`product_distribution`](@ref) instead.

