```julia
mutable struct CustomAlgorithm{R<:BaytesDiff.ℓDensityResult, T<:BaytesOptim.CustomAlgorithmTune} <: BaytesCore.AbstractAlgorithm
```

Stores information for proposal step.

# Fields

  * `result::BaytesDiff.ℓDensityResult`
  * `tune::BaytesOptim.CustomAlgorithmTune`
