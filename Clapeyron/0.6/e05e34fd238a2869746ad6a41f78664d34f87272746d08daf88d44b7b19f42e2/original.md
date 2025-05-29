```
Wilson <: ActivityModel
Wilson(components;
puremodel = PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `acentricfactor`: Single Parameter (`Float64`) - Acentric Factor
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `g`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter

## model parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `ZRA`: Single Parameter (`Float64`) - Rackett compresibility factor
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `g`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

Wilson activity model, with Rackett correlation for liquid volume:

```
Gᴱ = nRT∑xᵢlog(∑xⱼjΛᵢⱼ)
Λᵢⱼ = exp(-gᵢⱼ/T)*Vⱼ/Vᵢ
ZRAᵢ = 0.29056 - 0.08775ωᵢ
Vᵢ = (RTcᵢ/Pcᵢ)ZRAᵢ^(1 + (1-T/Tcᵢ)^2/7)
```

## Model Construction Examples

```
# Using the default database
model = Wilson(["water","ethanol"]) #Default pure model: PR
model = Wilson(["water","ethanol"],puremodel = BasicIdeal) #Using Ideal Gas for pure model properties
model = Wilson(["water","ethanol"],puremodel = PCSAFT) #Using Real Gas model for pure model properties

# Passing a prebuilt model

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = Wilson(["water","ethanol"],puremodel = my_puremodel)

# Using user-provided parameters

# Passing files or folders
model = Wilson(["water","ethanol"];userlocations = ["path/to/my/db","wilson.csv"])

# Passing parameters directly
model = Wilson(["water","ethanol"],
        userlocations = (g = [0.0 3988.52; 1360.117 0.0],
                        Tc = [647.13, 513.92],
                        Pc = [2.19e7, 6.12e6],
                        acentricfactor = [0.343, 0.643],
                        Mw = [18.015, 46.069])
                        )
```

## References

1. Wilson, G. M. (1964). Vapor-liquid equilibrium. XI. A new expression for the excess free energy of mixing. Journal of the American Chemical Society, 86(2), 127–130. [doi:10.1021/ja01056a002](https://doi.org/10.1021/ja01056a002)
