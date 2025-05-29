```
RackettLiquid(components;
userlocations::Vector{String}=String[],
verbose::Bool=false)
```

## Input parameters

  * `Tc`: Single Parameter (Float64) - Critical Temperature [K]
  * `Pc`: Single Parameter (Float64) - Critical Pressure [Pa]
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`

## Model Parameters

  * `Tc`: Single Parameter (Float64) - Critical Temperature [K]
  * `Pc`: Single Parameter (Float64) - Critical Pressure [Pa]
  * `Zc`: Single Parameter (Float64) - Critical Compressibility Factor

## Description

Rackett Equation of State for saturated liquids. it is independent of the pressure.

```
Tr = T/Tc
V = (R̄Tc/Pc)Zc^(1+(1-Tr)^(2/7))
```

## Model Construction Examples

```julia
# Using the default database
model = RackettLiquid("water") #single input
model = RackettLiquid(["water","ethanol"]) #multiple components

# User-provided parameters, passing files or folders
model = RackettLiquid(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

model = RackettLiquid(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Vc = [4.25e-5, 6.43e-5],
                        Pc = [2679000, 1296400])
                    )
```

## References

  * Rackett, H. G. (1970). Equation of state for saturated liquids. Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
