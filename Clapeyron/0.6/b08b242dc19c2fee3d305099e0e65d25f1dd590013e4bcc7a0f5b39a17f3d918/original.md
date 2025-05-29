```
Twu88Alpha::TwuAlpha

Twu88Alpha(components::Vector{String};
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `M`: Single Parameter
  * `N`: Single Parameter (optional)
  * `L`: Single Parameter

## Model Parameters

  * `M`: Single Parameter
  * `N`: Single Parameter
  * `L`: Single Parameter

## Description

Cubic alpha `(α(T))` model. Also known as Twu-88 alpha.

```
αᵢ = Trᵢ^(N*(M-1))*exp(L*(1-Trᵢ^(N*M))
N = 2
Trᵢ = T/Tcᵢ
```

if `N` is specified, it will be used instead of the default value of 2.

## Model Construction Examples

```
# Using the default database
alpha = Twu88Alpha("water") #single input
alpha = Twu88Alpha(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
alpha = Twu88Alpha(["neon","hydrogen"]; userlocations = ["path/to/my/db","twu88.csv"])

# Passing parameters directly
alpha = Twu88Alpha(["neon","hydrogen"];
    userlocations = (;L = [0.40453, 156.21],
                    M = [0.95861, -0.0062072],
                    N = [0.8396, 5.047]) #if we don't pass N, then is assumed N = 2
                )
```

## References

1. Twu, C. H., Lee, L. L., & Starling, K. E. (1980). Improved analytical representation of argon thermodynamic behavior. Fluid Phase Equilibria, 4(1–2), 35–44. [doi:10.1016/0378-3812(80)80003-3](https://doi.org/10.1016/0378-3812(80)80003-3)
