```julia
struct MAP{T<:Distributions.Distribution{Distributions.Univariate, Distributions.Continuous}, U<:Roots.AbstractSecantMethod} <: PersonParameters.PersonParameterAlgorithm
```

Maximum posterior estimation of person parameters of item response models. Use `prior` to specify the prior distribution of ability values.

## Fields

  * `prior`: The prior distribution of person abilities
  * `root_finding_alg`
