```
AsymmetricMixing <: MultiFluidDepartureModel
AsymmetricMixing(components;
userlocations = String[],
verbose = false)
```

## Input parameters

  * `beta_v`: Pair Parameter (`Float64`) - binary interaction parameter  (no units)
  * `gamma_v`: Pair Parameter (`Float64`) - binary interaction parameter  (no units)
  * `beta_T`: Pair Parameter (`Float64`) - binary interaction parameter  (no units)
  * `gamma_T`: Pair Parameter (`Float64`) - binary interaction parameter  (no units)

## Description

Asymmetric mixing rule for MultiParameter EoS models:

```
τ = T̄/T
δ = V̄/V
V̄ = ∑xᵢxⱼ * βᵛᵢⱼ * γᵛᵢⱼ * (xᵢ + xⱼ)/(xᵢ*βᵛᵢⱼ^2 + xⱼ) * Vᵣᵢⱼ
T̄ = ∑xᵢxⱼ * βᵛᵢⱼ * γᵀᵢⱼ * (xᵢ + xⱼ)/(xᵢ*βᵀᵢⱼ^2 + xⱼ) * Tᵣᵢⱼ
Vᵣᵢⱼ = 0.125*(∛Vcᵢ + ∛Vcⱼ)^3
Tᵣᵢⱼ = √(Tcᵢ*Tcⱼ)
```

With the asymmetry present in the β parameters:

```
βᵛᵢⱼ = 1/βᵛⱼᵢ
βᵀᵢⱼ = 1/βᵀⱼᵢ
```

If there is no data present, the parameters can be estimated:

  * Linear estimation:

```
βᵛᵢⱼ = βᵛᵢⱼ = 1
γᵛᵢⱼ = 4*(Vcᵢ + Vcⱼ)/(∛Vcᵢ + ∛Vcⱼ)^3
γᵀᵢⱼ = 0.5*(Tcᵢ + Tcⱼ)/√(Tcᵢ*Tcⱼ)
```

  * Lorentz-Berthelot Estimation:

```
βᵛᵢⱼ = βᵛᵢⱼ = γᵛᵢⱼ = γᵀᵢⱼ = 1
```

## References

1. R. Klimeck, Ph.D. dissertation, Ruhr-Universit¨at Bochum, 2000
