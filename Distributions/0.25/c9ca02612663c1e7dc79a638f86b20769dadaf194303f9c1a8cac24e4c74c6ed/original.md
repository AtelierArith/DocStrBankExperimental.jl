```
location{D<:AbstractMvLogNormal}(::Type{D},s::Symbol,m::AbstractVector,S::AbstractMatrix)
```

Calculate the location vector (the mean of the underlying normal distribution).

  * If `s == :meancov`, then m is taken as the mean, and S the covariance matrix of a lognormal distribution.
  * If `s == :mean | :median | :mode`, then m is taken as the mean, median or mode of the lognormal respectively, and S is interpreted as the scale matrix (the covariance of the underlying normal distribution).

It is not possible to analytically calculate the location vector from e.g., median + covariance, or from mode + covariance.
