MTTranslation <: MTTranslationModel

```
MTTranslation(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `acentricfactor`: Single Parameter (`Float64`)

## Description

Magoulas Tassios Translation model for cubics:

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = T₀ᵢ+(T̄cᵢ-T̄₀ᵢ)*exp(β*abs(1-Trᵢ))
Trᵢ = T/T̄cᵢ
T̄cᵢ = (RTcᵢ/Pcᵢ)*(0.3074-Zcᵢ)
T̄₀ᵢ = (RTcᵢ/Pcᵢ)*(-0.014471 + 0.067498ωᵢ - 0.084852ωᵢ^2 + 0.067298ωᵢ^3 - 0.017366ωᵢ^4)
Zcᵢ = 0.289 - 0.0701ωᵢ - 0.0207ωᵢ^2
βᵢ  = -10.2447 - 28.6312ωᵢ
```

## Model Construction Examples

```
# Using the default database
translation = MTTranslation("water") #single input
translation = MTTranslation(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
translation = MTTranslation(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# Passing parameters directly
translation = MTTranslation(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## References

1. Magoulas, K., & Tassios, D. (1990). Thermophysical properties of n-Alkanes from C1 to C20 and their prediction for higher ones. Fluid Phase Equilibria, 56, 119–140. [doi:10.1016/0378-3812(90)85098-u](https://doi.org/10.1016/0378-3812(90)85098-u)
