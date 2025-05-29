```
LCVMRule{γ} <: LCVMRuleModel

LCVMRule(components;
activity = Wilson,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

None

## Input models

  * `activity`: Activity Model

## Description

Linear Combination of Vidal and Michaelsen (LCVM) Mixing Rule

```
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ᾱᵢ  = aᵢαᵢ/bᵢRT
ċ = -q₁*Σᾱᵢxᵢ - q₂*Σᾱᵢxᵢ^2 - gᴱ/RT - ∑log(bᵢᵢ/b̄)
ā = b̄RT(-1.827[gᴱ/RT - 0.3∑log(bᵢᵢ/b̄)] + Σᾱᵢxᵢ)
```

## Model Construction Examples

```
# Using the default database
mixing = LCVMRule(["water","carbon dioxide"]) #default: Wilson Activity Coefficient.
mixing = LCVMRule(["water","carbon dioxide"],activity = NRTL) #passing another Activity Coefficient Model.
mixing = LCVMRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = LCVMRule(["water","ethanol"],activity = act_model)

# Using user-provided parameters

# Passing files or folders
mixing = LCVMRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
mixing = LCVMRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## References

1. Boukouvalas, C., Spiliotis, N., Coutsikos, P., Tzouvaras, N., & Tassios, D. (1994). Prediction of vapor-liquid equilibrium with the LCVM model: a linear combination of the Vidal and Michelsen mixing rules coupled with the original UNIFAC. Fluid Phase Equilibria, 92, 75–106. [doi:10.1016/0378-3812(94)80043-x](https://doi.org/10.1016/0378-3812(94)80043-x)
