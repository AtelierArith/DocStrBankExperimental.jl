```
TwuAlpha <: TwuAlphaModel
Twu91Alpha = TwuAlpha
TwuAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `M`: Single Parameter
  * `N`: Single Parameter
  * `L`: Single Parameter

## Description

Cubic alpha `(α(T))` model. Default for [`VTPR`](@ref) EoS. Also known as Twu-91 alpha

```
αᵢ = Trᵢ^(N*(M-1))*exp(L*(1-Trᵢ^(N*M))
Trᵢ = T/Tcᵢ
```

## Model Construction Examples

```
# Using the default database
alpha = TwuAlpha("water") #single input
alpha = Twu91Alpha("water") #same function
alpha = TwuAlpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = TwuAlpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","twu.csv"])

# Passing parameters directly
alpha = TwuAlpha(["neon","hydrogen"];
    userlocations = (;L = [0.40453, 156.21],
                    M = [0.95861, -0.0062072],
                    N = [0.8396, 5.047])
                )
```

## References

1. Twu, C. H., Lee, L. L., & Starling, K. E. (1980). Improved analytical representation of argon thermodynamic behavior. Fluid Phase Equilibria, 4(1–2), 35–44. [doi:10.1016/0378-3812(80)80003-3](https://doi.org/10.1016/0378-3812(80)80003-3)
