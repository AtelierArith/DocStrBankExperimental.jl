```
LJSAFTModel <: SAFTModel

LJSAFT(components;
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
  * `b`: Single Parameter (`Float64`) - Segment Volume [`dm^3/mol`]
  * `T_tilde`: Single Parameter (`Float64`) - Lennard-Jones attraction parameter  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater for energy(no units)
  * `zeta`: Pair Parameter (`Float64`) - Binary Interaction Paramater for volume (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `b`: Pair Parameter (`Float64`) - Mixed segment covolume `[dm^3/mol]`
  * `T_tilde`: Pair Parameter (`Float64`) - Mixed Lennard-Jones attraction parameter `[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Perturbed-Chain SAFT (PC-SAFT)

## References

1. Kraska, T., & Gubbins, K. E. (1996). Phase equilibria calculations with a modified SAFT equation of state. 1. Pure alkanes, alkanols, and water. Industrial & Engineering Chemistry Research, 35(12), 4727–4737. [doi:10.1021/ie9602320](https://doi.org/10.1021/ie9602320)
