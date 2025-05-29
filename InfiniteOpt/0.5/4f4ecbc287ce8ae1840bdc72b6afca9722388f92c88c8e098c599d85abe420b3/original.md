```
MultiDistributionDomain{T <: NonUnivariateDistribution} <: InfiniteArrayDomain
```

A `DataType` that stores the distribution characterizing a collection of infinite parameters that follows its form. This is for use with [`DependentParameters`](@ref).

**Fields**

  * `distribution::T` Distribution of the random parameters.
