```
YamadaGunnLiquid(components;
            userlocations::Vector{String}=String[],
            verbose::Bool=false)::RackettLiquid
```

## Input parameters

  * `Tc`: Single Parameter (Float64) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (Float64) - Critical Pressure `[Pa]`
  * `acentricfactor`: Single Parameter (`Float64`) - Acentric Factor

## Model Parameters

  * `Tc`: Single Parameter (Float64) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (Float64) - Critical Pressure `[Pa]`
  * `Zc`: Single Parameter (Float64) - Critical Compressibility Factor

## Description

The Yamada-Gunn equation of state is a modification of the Rackett equation of state that uses a different approach to calculate the compressibility factor `Zc`:

```
Tr = T/Tc
Zc = 0.29056 - 0.08775ω
V = (R̄Tc/Pc)Zc^(1+(1-Tr)^(2/7))
```

It can be used as a substitute of `RackettLiquid` when `Vc` is not known.

## Model Construction Examples

```julia
# Using the default database
model = YamadaGunnLiquid("water") #single input
model = YamadaGunnLiquid(["water","ethanol"]) #multiple components

# User-provided parameters, passing files or folders
model = YamadaGunnLiquid(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

model = YamadaGunnLiquid(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Pc = [2679000, 1296400],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## References

  * Rackett, H. G. (1970). Equation of state for saturated liquids. Journal of Chemical and Engineering Data, 15(4), 514–517. [doi:10.1021/je60047a012](https://doi.org/10.1021/je60047a012)
  * Gunn, R. D., & Yamada, T. (1971). A corresponding states correlation of saturated liquid volumes. AIChE Journal. American Institute of Chemical Engineers, 17(6), 1341–1345. [doi:10.1002/aic.690170613](https://doi.org/10.1002/aic.690170613)
