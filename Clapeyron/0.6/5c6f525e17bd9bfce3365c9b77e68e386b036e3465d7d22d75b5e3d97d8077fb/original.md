```
SAFTVRSMieModel <: SAFTModel

SAFTVRSMie(components;
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
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

SAFT-VR with Mie potential for the solid phase using WCA perturbation theory.

## References

1. Jalani, Y., Ramrattana, N., Walker, P.J., Riedemann, A., Galindo, A., Mater, O. K., & Müller, E. A. (2024). SAFT-VR Mie Equation of State for the Solid and Fluid Phases. (in preparation)
