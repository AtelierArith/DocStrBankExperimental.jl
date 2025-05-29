```
sCKSAFTModel <: CKSAFTModel

sCKSAFT(components; 
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
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Simplified Chen and Kreglewski SAFT (sCK-SAFT)

## References

1. Huang, S. H., & Radosz, M. (1990). Equation of state for small, large, polydisperse, and associating molecules. Industrial & Engineering Chemistry Research, 29(11), 2284–2294. [doi:10.1021/ie00107a014](https://doi.org/10.1021/ie00107a014)
2. Huang, S. H., & Radosz, M. (1991). Equation of state for small, large, polydisperse, and associating molecules: extension to fluid mixtures. Industrial & Engineering Chemistry Research, 30(8), 1994–2005. [doi:10.1021/ie00056a050](https://doi.org/10.1021/ie00056a050)
3. Fu, Y.-H., & Sandler, S. I. (1995). A simplified SAFT equation of state for associating compounds and mixtures. Industrial & Engineering Chemistry Research, 34(5), 1897–1909. [doi:10.1021/ie00044a042](https://doi.org/10.1021/ie00044a042)
