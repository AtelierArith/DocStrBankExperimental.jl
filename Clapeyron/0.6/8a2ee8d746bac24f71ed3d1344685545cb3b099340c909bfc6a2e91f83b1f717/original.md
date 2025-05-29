```
gErRule{γ} <: gErRuleModel

gErRule(components;
activity = NRTL,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

None

## Input models

  * `activity`: Activity Model

## Description

Mixing rule that uses the residual part of the activity coefficient model:

```
bᵢⱼ = ( (bᵢ^(2/3) + bⱼ^(2/3)) / 2 )^(3/2)
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā/b̄ = b̄RT*(∑xᵢaᵢ/bᵢ + gᴱᵣ/Λ
Λ = 1/(r₂ - r₁) * log((1 - r₂)/(1 - r₁))
```

## Model Construction Examples

```
# Using the default database
mixing = gErRule(["water","carbon dioxide"]) #default: NRTL Activity Coefficient.
mixing = gErRule(["water","carbon dioxide"],activity = Wilson) #passing another Activity Coefficient Model.
mixing = gErRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = gErRule(["water","ethanol"],activity = act_model)

# Using user-provided parameters

# Passing files or folders
mixing = gErRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
mixing = gErRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## References

1. Piña-Martinez, A., Privat, R., Nikolaidis, I. K., Economou, I. G., & Jaubert, J.-N. (2021). What is the optimal activity coefficient model to be combined with the translated–consistent Peng–Robinson equation of state through advanced mixing rules? Cross-comparison and grading of the Wilson, UNIQUAC, and NRTL aE models against a benchmark database involving 200 binary systems. Industrial & Engineering Chemistry Research, 60(47), 17228–17247. [doi:10.1021/acs.iecr.1c03003](https://doi.org/10.1021/acs.iecr.1c03003)
