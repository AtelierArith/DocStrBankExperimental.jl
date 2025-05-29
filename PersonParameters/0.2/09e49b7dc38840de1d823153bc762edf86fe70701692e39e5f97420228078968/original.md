```julia
struct EAP{T<:Distributions.Distribution{Distributions.Univariate, Distributions.Continuous}, U<:Real} <: PersonParameters.PersonParameterAlgorithm
```

Expected posterior estimation of person parameters of item response models. Use `prior` to specify the prior distribution of ability values.

`domain` can be used to restrict the domain for numerical integration. Defaults to `extrema(prior)`, c.f. the whole support of the prior distribution.

## Fields

  * `prior`: the prior distribution of person abilities
  * `domain`: the integration domain
