```
structSAFTgammaMie <: SAFTgammaMieModel

structSAFTgammaMie(components; 
idealmodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
epsilon_mixing = :default,
assoc_options = AssocOptions())
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `vst`: Single Parameter (`Float64`) - Number of segments (no units)
  * `S`: Single Parameter (`Float64`) - Shape factor for segment (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Model Parameters

  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `shapefactor`: Single Parameter (`Float64`) - Shape factor for segment (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume
  * `mixed_segment`: Mixed Group Contribution Parameter: ∑nᵢₖνₖmₖ

## Input models

  * `idealmodel`: Ideal Model

## Description

s-SAFT-γ-Mie EoS

## References

1. Shaahmadi,, F., Hurter, R.M., Burger, A.J., Cripwell, J.T. (2021). Improving the SAFT-γ Mie equation of state to account for functional group interactions in a structural (s-SAFT-γ Mie) framework: Linear and branched alkanes. The Journal of Chemical Physics, 154, 244102. [doi:10.1063/5.0048315 ](https://doi.org/10.1063/5.0048315 )
2. Schulze-Hulbe, A., Shaahmadi, F., Burger, A.J., Cripwell, J.T. (2022). Extending the Structural (s)-SAFT-γ Mie Equation of State to Primary Alcohols. Industrial & Engineering Chemistry Research, 61 (33), 12208-12228. [doi:10.1021/acs.iecr.2c00198](https://doi.org/10.1021/acs.iecr.2c00198)
