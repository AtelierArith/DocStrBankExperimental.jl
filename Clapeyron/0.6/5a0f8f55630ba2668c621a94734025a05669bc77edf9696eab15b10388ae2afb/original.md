```
RackettTranslation <: RackettTranslationModel

RackettTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`

## Model Parameters

  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`
  * `v_shift`: Single Parameter (`Float64`) - Volume shift `[m³/mol]`

## Description

Rackett Translation model for cubics:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = 0.40768*RTcᵢ/Pcᵢ*(0.29441-Zcᵢ)
Zcᵢ = Pcᵢ*Vcᵢ/(RTcᵢ)
```

## Model Construction Examples

```
# Using the default database
translation = RackettTranslation("water") #single input
translation = RackettTranslation(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
translation = RackettTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/Vc.csv"])

# Passing parameters directly
translation = RackettTranslation(["neon","hydrogen"];userlocations = (;Vc = [4.25e-5, 6.43e-5]))
```

## References

1. Rackett, H. G. (1970). Equation of state for saturated liquids. Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
