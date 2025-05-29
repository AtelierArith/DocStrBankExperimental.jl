```
NormalWeightedMeanPrecision{T <: Real} <: ContinuousUnivariateDistribution
```

A normal distribution parametrized by its natural parameters: the weighted mean `xi` and precision `w`.

# Fields

  * `xi::T`: The weighted mean of the normal distribution. `xi` is computed as `w * μ`, where `μ` is the mean of the distribution.
  * `w::T`: The precision (inverse variance) of the normal distribution.
