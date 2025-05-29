```
PenelouxTranslation <: PenelouxTranslationModel

PenelouxTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`

## Model Parameters

  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`
  * `v_shift`: Single Parameter (`Float64`) - Volume shift `[m³/mol]`

## Description

Peneloux Translation model for cubics:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = -0.252*RTcᵢ/Pcᵢ*(1.5448Zcᵢ - 0.4024)
Zcᵢ = Pcᵢ*Vcᵢ/(RTcᵢ)
```

## Model Construction Examples

```
# Using the default database
translation = PenelouxTranslation("water") #single input
translation = PenelouxTranslation(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
translation = PenelouxTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/Vc.csv"])

# Passing parameters directly
translation = PenelouxTranslation(["neon","hydrogen"];userlocations = (;Vc = [4.25e-5, 6.43e-5]))
```

## References

1. Péneloux A, Rauzy E, Fréze R. (1982) A consistent correction for Redlich‐Kwong‐Soave volumes. Fluid Phase Equilibria 1, 8(1), 7–23. [doi:10.1016/0378-3812(82)80002-2](https://doi.org/10.1016/0378-3812(82)80002-2)
