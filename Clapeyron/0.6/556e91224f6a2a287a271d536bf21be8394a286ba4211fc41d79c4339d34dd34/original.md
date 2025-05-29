```
QPCPSAFTModel <: PCPSAFTModel

QPCPSAFT(components;
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
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `quadrupole`: Single Parameter (`Float64`) - Quadrupole moment `[DA°]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `quadrupole`: Single Parameter (`Float64`) - Quadrupole moment `[DA°]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Polar Perturbed-Chain SAFT, including Quadrupolar interaction contributions (Q-PCP-SAFT)

## References

1. Gross, J. (2005). An equation-of-state contribution for polar components: Quadrupolar molecules. AIChE Journal, 51(9), 2556-2568. [doi:10.1002/aic.10502](https://doi.org/10.1002/aic.10502)
2. Gross, J., & Vrabec, J. (2008). Vapor−Liquid Equilibria Simulation and an Equation of State Contribution for Dipole−Quadrupole Interactions. J. Phys. Chem. B, 112(1), 51-60. [doi:10.1021/jp072619u](https://doi.org/10.1021/jp072619u)
