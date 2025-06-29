```
tcPRWilsonRes <: WilsonModel
tcPRWilsonRes(components;
puremodel = BasicIdeal,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `g`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Interaction Parameter
  * `v`: Single Parameter (optional) (`Float64`) - individual volumes.

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

tc-PR-Wilson residual activity model, meant to used in combination with the tc-PR cubic EoS:

```
Gᴱᵣ = nRT( ∑xᵢlog(∑xⱼjΛᵢⱼ) - ∑xᵢ*(log(vᵢ/v) )
Λᵢⱼ = exp(-gᵢⱼ/T)*Vⱼ/Vᵢ 
```

## Model Construction Examples

```
# Using the default database
model = tcPRWilsonRes(["water","ethanol"]) #Default pure model: PR
model = tcPRWilsonRes(["water","ethanol"],puremodel = BasicIdeal) #Using Ideal Gas for pure model properties
model = tcPRWilsonRes(["water","ethanol"],puremodel = PCSAFT) #Using Real Gas model for pure model properties

# Passing a prebuilt model

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = tcPRWilsonRes(["water","ethanol"],puremodel = my_puremodel)

# Using user-provided parameters

# Passing files or folders
model = tcPRWilsonRes(["water","ethanol"];userlocations = ["path/to/my/db","tcpr_wilson.csv"])

# Passing parameters directly
model = tcPRWilsonRes(["water","ethanol"],userlocations = (;g = [0.0 3988.52; 1360.117 0.0]))
```

## References

1. Wilson, G. M. (1964). Vapor-liquid equilibrium. XI. A new expression for the excess free energy of mixing. Journal of the American Chemical Society, 86(2), 127–130. [doi:10.1021/ja01056a002](https://doi.org/10.1021/ja01056a002)
2. Piña-Martinez, A., Privat, R., Nikolaidis, I. K., Economou, I. G., & Jaubert, J.-N. (2021). What is the optimal activity coefficient model to be combined with the translated–consistent Peng–Robinson equation of state through advanced mixing rules? Cross-comparison and grading of the Wilson, UNIQUAC, and NRTL aE models against a benchmark database involving 200 binary systems. Industrial & Engineering Chemistry Research, 60(47), 17228–17247. [doi:10.1021/acs.iecr.1c03003](https://doi.org/10.1021/acs.iecr.1c03003)
