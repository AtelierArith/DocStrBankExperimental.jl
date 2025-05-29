```
aspenNRTL <: ActivityModel

function aspenNRTL(components;
puremodel=PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `a0`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `a1`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `t0`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `t1`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `t2`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `t3`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

NRTL (Non Random Two Fluid) activity model:

```
Gᴱ = nRT∑[xᵢ(∑τⱼᵢGⱼᵢxⱼ)/(∑Gⱼᵢxⱼ)]
Gᵢⱼ exp(-αᵢⱼτᵢⱼ)
αᵢⱼ = αᵢⱼ₀ + αᵢⱼ₁T
τᵢⱼ = tᵢⱼ₀ + tᵢⱼ₁/T + tᵢⱼ₂*ln(T) + tᵢⱼ₃*T
```

## Model Construction Examples

```
# Using the default database
model = aspenNRTL(["water","ethanol"]) #Default pure model: PR
model = aspenNRTL(["water","ethanol"],puremodel = BasicIdeal) #Using Ideal Gas for pure model properties
model = aspenNRTL(["water","ethanol"],puremodel = PCSAFT) #Using Real Gas model for pure model properties
# Passing a prebuilt model

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = aspenNRTL(["water","ethanol"],puremodel = my_puremodel)

# Using user-provided parameters

# Passing files or folders
model = aspenNRTL(["water","ethanol"];userlocations = ["path/to/my/db","nrtl.csv"])

# Passing parameters directly
model = aspenNRTL(["water","acetone"],
userlocations = (a0 = [0.0 0.228632; 0.228632 0.0],
                a1 = [0.0 0.000136; 0.000136 0.0],
                t0 = [0.0 13.374756; 16.081848 0.0],
                t1 = [0.0 -415.527344; -88.8125 0.0],
                t2 = [0.0 -1.913689; -2.930901 0.0],
                t3 = [0.0 0.00153; 0.005305 0.0])
            )
```

## References

1. Renon, H., & Prausnitz, J. M. (1968). Local compositions in thermodynamic excess functions for liquid mixtures. AIChE journal. American Institute of Chemical Engineers, 14(1), 135–144. [doi:10.1002/aic.690140124](https://doi.org/10.1002/aic.690140124)
