```julia
struct PMCMCTune{T<:ModelWrappers.Tagged} <: BaytesCore.AbstractTune
```

PMCMC tuning container.

# Fields

  * `tagged::ModelWrappers.Tagged`: Tagged Model parameter.
