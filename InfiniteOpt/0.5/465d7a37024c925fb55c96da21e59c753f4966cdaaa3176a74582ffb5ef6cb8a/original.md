```
IntervalDomain <: InfiniteScalarDomain
```

A `DataType` that stores the lower and upper interval bounds for infinite parameters that are continuous over a certain that interval. This is for use with a [`IndependentParameter`](@ref).

**Fields**

  * `lower_bound::Float64` Lower bound of the infinite parameter.
  * `upper_bound::Float64` Upper bound of the infinite parameter.
