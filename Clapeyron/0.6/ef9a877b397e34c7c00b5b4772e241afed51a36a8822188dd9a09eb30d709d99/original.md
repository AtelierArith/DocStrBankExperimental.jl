```
RKPRAlpha <: RKPRAlphaModel

RKPRAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `acentricfactor`: Single Parameter (`Float64`)

## Description

Cubic alpha `(α(T))` model. Default for [`RKPR`](@ref) EoS.

```
αᵢ = (3/(2 + Trᵢ))^kᵢ
kᵢ = (12.504Zc -2.7238) + (7.4513*Zc + 1.9681)ωᵢ + (-2.4407*Zc + 0.0017)ωᵢ^2
Trᵢ = T/Tcᵢ
```

## Model Construction Examples

```
# Using the default database
alpha = RKPRAlpha("water") #single input
alpha = RKPRAlpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = RKPRAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# Passing parameters directly
alpha = RKPRAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
