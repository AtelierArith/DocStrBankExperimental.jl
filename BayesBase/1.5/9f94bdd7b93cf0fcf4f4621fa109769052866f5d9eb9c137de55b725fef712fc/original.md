```
ContinuousUnivariateLogPdf{ D <: DomainSets.Domain, F } <: AbstractContinuousGenericLogPdf
```

Generic continuous univariate distribution in a form of domain specification and logpdf function. Can be used in cases where no  known analytical distribution available. 

# Arguments

  * `domain`: domain specificatiom from `DomainSets.jl` package, by default the `domain` is set to `DomainSets.FullSpace()`. Use `BayesBase.UnspecifiedDomain()` to bypass domain checks.
  * `logpdf`: callable object that represents the logdensity. Can be un-normalised.
