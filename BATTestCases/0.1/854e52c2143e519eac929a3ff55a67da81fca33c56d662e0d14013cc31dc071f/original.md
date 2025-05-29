```
struct FunnelDistribution <: Distribution{Multivariate,Continuous}
```

*Experimental feature, not part of stable public API.*

A funnel distribution (see [Caldwell et al.](https://arxiv.org/abs/1808.08051) for definition).

Constructors:

  * `FunnelDistribution(; a::Real = 1.0, b::Real = 0.5, n::Integer = 3)`

Fields:

  * `a::Real`: Variance of the dominant normal distribution.
  * `b::Real`: Variance of the supporting normal distributions.
  * `n::Integer`: Number of dimensions.
