```
SoaveAlpha <: SoaveAlphaModel

SoaveAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `acentricfactor`: Single Parameter (`Float64`)

## Description

Cubic alpha `(α(T))` model. Default for [`SRK`](@ref) EoS.

```
αᵢ = (1+mᵢ(1-√(Trᵢ)))^2
Trᵢ = T/Tcᵢ
mᵢ = 0.480 + 1.547ωᵢ - 0.176ωᵢ^2
```

To use different polynomial coefficients for `mᵢ`, overload `Clapeyron.α_m(::CubicModel,::SoaveAlphaModel) = (c₁,c₂,...cₙ)`

## Model Construction Examples

```
# Using the default database
alpha = SoaveAlpha("water") #single input
alpha = SoaveAlpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = SoaveAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical/acentric.csv"])

# Passing parameters directly
alpha = SoaveAlpha(["neon","hydrogen"];userlocations = (;acentricfactor = [-0.03,-0.21]))
```
