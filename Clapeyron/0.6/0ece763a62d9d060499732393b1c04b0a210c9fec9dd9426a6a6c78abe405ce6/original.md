```
SAFTVRQMieModel <: SAFTVRMieModel

SAFTVRQMie(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
fh_order = :fh2,
verbose = false)
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`

## Model Parameters

  * `Mw`: Pair Parameter (`Float64`) - Mixed Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`

## Input models

  * `idealmodel`: Ideal Model

## Description

Quantum-Corrected SAFT-VR Mie. In particular,The Feynman–Hibbs correction order can be modified by passing the `fh_order` keyword argument. The default is 2nd order (`:fh2`), but 1st order (`:fh1`) is also available.

## References

1. Aasen, A., Hammer, M., Ervik, Å., Müller, E. A., & Wilhelmsen, Ø. (2019). Equation of state and force fields for Feynman–Hibbs-corrected Mie fluids. I. Application to pure helium, neon, hydrogen, and deuterium. The Journal of Chemical Physics, 151(6), 064508. [doi:10.1063/1.5111364](https://doi.org/10.1063/1.5111364)
2. Aasen, A., Hammer, M., Müller, E. A., & Wilhelmsen, Ø. (2020). Equation of state and force fields for Feynman-Hibbs-corrected Mie fluids. II. Application to mixtures of helium, neon, hydrogen, and deuterium. The Journal of Chemical Physics, 152(7), 074507. [doi:10.1063/1.5136079](https://doi.org/10.1063/1.5136079)
