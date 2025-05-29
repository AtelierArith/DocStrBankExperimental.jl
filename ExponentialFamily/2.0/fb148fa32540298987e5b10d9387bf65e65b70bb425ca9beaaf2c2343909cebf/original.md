```
NormalGamma{T <: Real} <: ContinuousMultivariateDistribution
```

A normal-gamma distribution, where `T` is a real number. This distribution is a joint distribution of a normal random variable with mean `μ` and precision `λ`, and a gamma-distributed random variable with shape `α` and rate `β`.

# Fields

  * `μ::T`: The mean of the normal distribution.
  * `λ::T`: The precision of the normal distribution.
  * `α::T`: The shape parameter of the gamma distribution.
  * `β::T`: The rate parameter of the gamma distribution.
