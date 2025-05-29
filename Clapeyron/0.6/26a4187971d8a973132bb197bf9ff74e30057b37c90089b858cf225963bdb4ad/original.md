```
PTVAlpha <: PTVAlphaModel

PTVAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `acentricfactor`: Single Parameter (`Float64`)

## Description

Cubic alpha `(α(T))` model. Default for [`PTV`](@ref) EoS.

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.46283 + 3.58230Zcᵢ*ωᵢ - 8.19417(Zcᵢ*ωᵢ)^2
```

## Model Construction Examples

```
# Using the default database
alpha = PTVAlpha("water") #single input
alpha = PTVAlpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = PTVAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# Passing parameters directly
alpha = PTVAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
