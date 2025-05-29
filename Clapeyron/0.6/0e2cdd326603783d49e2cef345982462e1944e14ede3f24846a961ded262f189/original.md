```
UMRRule{γ} <: UMRRuleModel

UMRRule(components;
activity = UNIFAC,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

None

## Input models

  * `activity`: Activity Model

## Description

Mixing Rule used by the Universal Mixing Rule Peng-Robinson [`UMRPR`](@ref) equation of state.

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)((√bᵢ +√bⱼ)/2)^2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄RT(∑[xᵢaᵢᵢαᵢ/(RTbᵢᵢ)] - [gᴱ/RT]/0.53)

## Model Construction Examples
```

# Note: this model was meant to be used exclusively with the UNIFAC activity model.

# Using the default database

mixing = VTPRRule(["water","carbon dioxide"]) #default: UNIFAC Activity Coefficient. mixing = VTPRRule(["water","carbon dioxide"],activity = NRTL) #passing another Activity Coefficient Model mixing = VTPRRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = ogUNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act*model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0])) mixing = VTPRRule(["water","ethanol"],activity = act*model)

# Using user-provided parameters

# Passing files or folders

mixing = VTPRRule(["water","ethanol"]; activity = NRTL, activity*userlocations = ["path/to/my/db","nrtl*ge.csv"])

# Passing parameters directly

mixing = VTPRRule(["water","ethanol"];                 activity = NRTL,                 userlocations = (a = [0.0 3.458; -0.801 0.0],                     b = [0.0 -586.1; 246.2 0.0],                     c = [0.0 0.3; 0.3 0.0])                 )

```

```
