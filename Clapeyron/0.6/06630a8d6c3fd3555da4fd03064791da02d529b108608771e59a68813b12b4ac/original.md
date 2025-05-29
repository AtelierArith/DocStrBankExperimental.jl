```
SAFTVRSWModel <: SAFTModel

SAFTVRSW(components;
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
  * `lambda`: Single Parameter (`Float64`) - Soft Well range parameter (no units)
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `l`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `lambda`: Pair Parameter (`Float64`) - Mixed Soft Well range parameter (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

SAFT, Variable Range (VR) ,Square Well (SW)

## References

1. Gil-Villegas, A., Galindo, A., Whitehead, P. J., Mills, S. J., Jackson, G., & Burgess, A. N. (1997). Statistical associating fluid theory for chain molecules with attractive potentials of variable range. The Journal of chemical physics, 106(10), 4168–4186. [doi:10.1063/1.473101](https://doi.org/10.1063/1.473101)
