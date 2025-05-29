```
MHV2Rule{γ} <: MHV2RuleModel

MHV2Rule(components;
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

Modified Huron-Vidal Mixing Rule, Second Order.

```
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ᾱᵢ  = aᵢαᵢ/bᵢRT
ċ = -q₁*Σᾱᵢxᵢ - q₂*Σᾱᵢxᵢ^2 - gᴱ/RT - ∑log(bᵢᵢ/b̄)
ā = (-q₁ - √(q₁^2 - 4q₂ċ))/(2q₂)

if the model is Peng-Robinson:
    q₁ = -0.4347, q₂ = -0.003654
if the model is Redlich-Kwong:
    q₁ = -0.4783, q₂ = -0.0047
    (-0.4783,-0.0047)
```

to use different values for `q₁` and `q₂`, overload `Clapeyron.MHV1q(::CubicModel,::MHV2Model) = (q₁,q₂)`

## Model Construction Examples

```
# Using the default database
mixing = MHV2Rule(["water","carbon dioxide"]) #default: Wilson Activity Coefficient.
mixing = MHV2Rule(["water","carbon dioxide"],activity = NRTL) #passing another Activity Coefficient Model.
mixing = MHV2Rule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = MHV2Rule(["water","ethanol"],activity = act_model)

# Using user-provided parameters

# Passing files or folders
mixing = MHV2Rule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
mixing = MHV1Rule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## References

1. Michelsen, M. L. (1990). A modified Huron-Vidal mixing rule for cubic equations of state. Fluid Phase Equilibria, 60(1–2), 213–219. [doi:10.1016/0378-3812(90)85053-d](https://doi.org/10.1016/0378-3812(90)85053-d)
