```
KUAlpha <: AlphaModel

KUAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `acentricfactor`: Single Parameter (`Float64`)

## Description

Cubic alpha `(α(T))` model. Default for [`KU`](@ref) EoS.

For `Tr < 1`

```
αᵢ = (1+mᵢ(1-√(Trᵢ))^nᵢ)^2
Trᵢ = T/Tcᵢ
mᵢ = 0.37790 + 1.51959ωᵢ - 0.46904ωᵢ^2 + 0.015679ωᵢ^3
nᵢ = 0.97016 + 0.05495ωᵢ - 0.1293ωᵢ^2 + 0.0172028ωᵢ^3
```

For `Tr > 1` is a 6th order taylor expansion around `T = Tc`.

## Model Construction Examples

```
# Using the default database
alpha = KUAlpha("water") #single input
alpha = KUAlpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = KUAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# Passing parameters directly
alpha = KUAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```

## References

1. Kumar, A., & Upadhyay, R. (2021). A new two-parameters cubic equation of state with benefits of three-parameters. Chemical Engineering Science, 229(116045), 116045. [doi:10.1016/j.ces.2020.116045](https://doi.org/10.1016/j.ces.2020.116045)
