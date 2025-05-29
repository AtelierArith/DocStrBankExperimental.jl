```
ContinuousMultivariateLogPdf{ D <: DomainSets.Domain, F } <: AbstractContinuousGenericLogPdf
```

Generic continuous multivariate distribution in a form of domain specification and logpdf function. Can be used in cases where no  known analytical distribution available. 

# Arguments

  * `domain`: multidimensional domain specification from `DomainSets.jl` package. Use `BayesBase.UnspecifiedDomain()` to bypass domain checks.
  * `logpdf`: callable object that accepts an `AbstractVector` as an input and represents the logdensity. Can be un-normalised.
