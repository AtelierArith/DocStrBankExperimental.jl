```
SAFTVRMieGVModel <: SAFTModel
SAFTVRMieGV(components;
idealmodel=BasicIdeal,
userlocations=String[],
ideal_userlocations=String[],
verbose=false,
assoc_options = AssocOptions()) # SS: is it possible to add another parameter here to select/deselect DQ term?
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `lambda_a`: Pair Parameter (`Float64`) - Attractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `np` : Single Parameter (`Float64`) - number of dipolar segments (no units)
  * `quadrupole`: Single Parameter (`Float64`) - Quadrupole moment `[DA°]`
  * `nQ` : Single Parameter (`Float64`) - number of quadrupolar segments (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `lambda_a`: Pair Parameter (`Float64`) - Attractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `np` : Single Parameter (`Float64`) - number of dipolar segments (no units)
  * `quadrupole`: Single Parameter (`Float64`) - Quadrupole moment `[DA°]`
  * `nQ` : Single Parameter (`Float64`) - number of quadrupolar segments (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Polar SAFT-VR with Mie potential, including Dipolar and Quadrupolar interaction contributions (SAFT-VR Mie GV)

## References

Polar terms:

1. Gross, J. (2005). An equation-of-state contribution for polar components: Quadrupolar molecules. AIChE Journal, 51(9), 2556-2568. [doi:10.1002/aic.10502](https://doi.org/10.1002/aic.10502)
2. Gross, J., & Vrabec, J. (2006). An equation-of-state contribution for polar components: Dipolar molecules. AIChE Journal, 52(3), 856-1282. [doi:10.1002/aic.10683](https://doi.org/10.1002/aic.10683)
3. Gross, J., & Vrabec, J. (2008). Vapor−Liquid Equilibria Simulation and an Equation of State Contribution for Dipole−Quadrupole Interactions. J. Phys. Chem. B, 112(1), 51-60. [doi:10.1021/jp072619u](https://doi.org/10.1021/jp072619u)

Implemented in SAFT-VR Mie:

1. Cripwell et al. (2017). SAFT-VR-Mie with an incorporated polar term for accurate holistic prediction of the thermodynamic properties of polar components. Fluid Phase Equilibria, 455, 24-42. [doi:10.1016/j.fluid.2017.09.027](https://doi.org/10.1016/j.fluid.2017.09.027)
2. Smith et al. (2020). A Quadrupolar SAFT-VR Mie Approach to Modeling Binary Mixtures of CO2 or Benzene with n-Alkanes or 1-Alkanols. J. Chem. Eng. Data, 65(12), 5778-5800. [doi:10.1021/acs.jced.0c00705](https://doi.org/10.1021/acs.jced.0c00705)
