```
UniDistributionDomain{T <: Distributions.UnivariateDistribution} <: InfiniteScalarDomain
```

A `DataType` that stores the distribution characterizing an infinite parameter that is random. This is for use with a [`IndependentParameter`](@ref).

**Fields**

  * `distribution::T` Distribution of the random parameter.
