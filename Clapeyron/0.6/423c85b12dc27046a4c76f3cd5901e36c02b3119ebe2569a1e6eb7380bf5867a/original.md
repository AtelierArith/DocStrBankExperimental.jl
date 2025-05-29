```
CPAAlpha <: CPAAlphaModel

CPAAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `c1`: Single Parameter (`Float64`)

## Description

Cubic alpha `(α(T))` model. Default for `CPA` EoS.

```
αᵢ = (1+c¹ᵢ(1-√(Trᵢ)))^2
```

## Model Construction Examples

```
# Using the default database
alpha = CPAAlpha("water") #single input
alpha = CPAAlpha(["water","carbon dioxide"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = CPAAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","cpa/alpha.csv"])

# Passing parameters directly
alpha = CPAAlpha(["water","carbon dioxide"];userlocations = (;c1 = [0.67,0.76]))
```
