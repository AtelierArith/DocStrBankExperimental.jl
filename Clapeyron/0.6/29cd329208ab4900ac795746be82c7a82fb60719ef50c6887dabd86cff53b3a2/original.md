```
BACKSAFTModel <: SAFTModel

BACKSAFT(components; 
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
  * `vol`: Single Parameter (`Float64`) - Segment Volume [`dm^3`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K/mol]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `c`: Single Parameter (`Float64`) - Adjustable parameter (no units)
  * `alpha`: Single Parameter (`Float64`) - Non-spherical deviation (no units)

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `c`: Single Parameter (`Float64`) - Adjustable parameter (no units)
  * `alpha`: Single Parameter (`Float64`) - Non-spherical deviation (no units)

## Input models

  * `idealmodel`: Ideal Model

## Description

BACKSAFT

## References

1. Mi, J.-G., Chen, J., Gao, G.-H., & Fei, W.-Y. (2002). Equation of state extended from SAFT with improved results for polar fluids across the critical point. Fluid Phase Equilibria, 201(2), 295–307. [doi:10.1016/s0378-3812(02)00093-6](https://doi.org/10.1016/s0378-3812(02)00093-6)
