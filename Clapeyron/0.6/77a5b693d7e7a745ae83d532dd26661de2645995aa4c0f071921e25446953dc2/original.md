```
SanchezLacombe(components;
idealmodel = BasicIdeal,
mixing = SLk0k1lMixingRule,
userlocations = String[],
ideal_userlocations = String[],
mixing_userlocations = String[],
reference_state = false,
verbose = false)
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `epsilon`: Single Parameter (`Float64`) - Nonbonded interaction energy per monomer `[J/mol]`
  * `vol`: Single Parameter (`Float64`) - Closed Packed Specific volume `[m^3/mol]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Nonbonded interaction energy per monomer `[J/mol]`
  * `vol`: Pair Parameter (`Float64`) - Closed Packed Specific volume `[m^3/mol]`

## Input models

  * `idealmodel`: Ideal Model
  * `mixing`: Mixing model

## Description

Sanchez-Lacombe Lattice Fluid Equation of State.

```
xᵢ = zᵢ/∑zᵢ
r̄ = ∑xᵢrᵢ
vᵣ,εᵣ = mix_vε(model,V,T,z,model.mixing,r̄,∑zᵢ)
ρ̃ = r̄*vᵣ/v
T̃ = R̄*T/εᵣ
aᵣ = r̄*(- ρ̃ /T̃ + (1/ρ̃  - 1)*log(1 - ρ̃ ) + 1)
```

## References

1. Neau, E. (2002). A consistent method for phase equilibrium calculation using the Sanchez–Lacombe lattice–fluid equation-of-state. Fluid Phase Equilibria, 203(1–2), 133–140. [doi:10.1016/s0378-3812(02)00176-0](https://doi.org/10.1016/s0378-3812(02)00176-0)
