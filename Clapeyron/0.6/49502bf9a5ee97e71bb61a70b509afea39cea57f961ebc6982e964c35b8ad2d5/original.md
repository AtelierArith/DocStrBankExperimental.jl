```
PSRKRule{γ} <: MHV1RuleModel

PSRKRule(components;
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

Mixing Rule used by the Predictive Soave-Redlich-Kwong [`PSRK`](@ref) EoS, derived from the First Order modified Huron-Vidal Mixing Rule.

## Model Construction Examples

```
# Note: this model was meant to be used exclusively with the PSRKUNIFAC activity model.

# Using the default database
mixing = PSRKRule(["water","carbon dioxide"]) #default: PSRKUNIFAC Activity Coefficient.
mixing = PSRKRule(["water","carbon dioxide"],activity = NRTL) #passing another Activity Coefficient Model
mixing = PSRKRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = PSRKRule(["water","ethanol"],activity = act_model)

# Using user-provided parameters

# Passing files or folders
mixing = PSRKRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
mixing = PSRKRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```
