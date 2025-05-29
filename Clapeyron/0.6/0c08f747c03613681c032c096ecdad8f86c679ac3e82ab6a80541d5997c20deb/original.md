```
CPPCSAFTModel <: PCSAFTModel

CPPCSAFT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Pair Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Critical Point-Based PC-SAFT (CP-PC-SAFT)

## References

1. Polishuk, I. (2014). Standardized critical point-based numerical solution of statistical association fluid theory parameters: The perturbed chain-statistical association fluid theory equation of state revisited. Industrial & Engineering Chemistry Research, 53(36), 14127–14141. [doi:10.1021/ie502633e](https://doi.org/10.1021/ie502633e)
