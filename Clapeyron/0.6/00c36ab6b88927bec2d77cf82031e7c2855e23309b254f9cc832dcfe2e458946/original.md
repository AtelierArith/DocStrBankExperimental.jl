```
LeeKeslerSat <: SaturationModel

LeeKeslerSat(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `acentricfactor`: Single Parameter (`Float64`) - acentric factor

## Description

Lee-Kesler correlation for saturation pressure:

```
psat(T) = f₀ + ω•f₁
Tr = T/Tc
f₀ = 5.92714 - 6.09648/Tr - 1.28862•log(Tr) + 0.169347•Tr⁶
f₁ = 15.2518 - 15.6875/Tr - 13.4721•log(Tr) + 0.43577•Tr⁶
```

## Model Construction Examples

```julia
# Using the default database
sat = LeeKeslerSat("water") #single input
sat = LeeKeslerSat(["water","ethanol"]) #multiple components

# User-provided parameters, passing files or folders
sat = LeeKeslerSat(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

sat = LeeKeslerSat(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## References

1. Lee, B. I., & Kesler, M. G. (1975). A generalized thermodynamic correlation based on three-parameter corresponding states. AIChE journal. American Institute of Chemical Engineers, 21(3), 510–527. [doi:10.1002/aic.690210313](https://doi.org/10.1002/aic.690210313)
