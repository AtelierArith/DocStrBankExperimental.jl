```
NRTL <: ActivityModel

function NRTL(components;
puremodel=PR,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `a`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `b`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `c`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

NRTL (Non Random Two Fluid) activity model:

```
Gᴱ = nRT∑[xᵢ(∑τⱼᵢGⱼᵢxⱼ)/(∑Gⱼᵢxⱼ)]
Gᵢⱼ exp(-cᵢⱼτᵢⱼ)
τᵢⱼ = aᵢⱼ + bᵢⱼ/T
```

## Model Construction Examples

```
# Using the default database
model = NRTL(["water","ethanol"]) #Default pure model: PR
model = NRTL(["water","ethanol"],puremodel = BasicIdeal) #Using Ideal Gas for pure model properties
model = NRTL(["water","ethanol"],puremodel = PCSAFT) #Using Real Gas model for pure model properties

# Passing a prebuilt model

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = NRTL(["water","ethanol"],puremodel = my_puremodel)

# Using user-provided parameters

# Passing files or folders
model = NRTL(["water","ethanol"];userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
model = NRTL(["water","ethanol"],
userlocations = (a = [0.0 3.458; -0.801 0.0],
                b = [0.0 -586.1; 246.2 0.0],
                c = [0.0 0.3; 0.3 0.0])
            )
```

## References

1. Renon, H., & Prausnitz, J. M. (1968). Local compositions in thermodynamic excess functions for liquid mixtures. AIChE journal. American Institute of Chemical Engineers, 14(1), 135–144. [doi:10.1002/aic.690140124](https://doi.org/10.1002/aic.690140124)
