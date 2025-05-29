```
VTPRRule{γ} <: VTPRRuleModel

VTPRRule(components;
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

Mixing Rule used by the Volume-translated Peng-Robinson [`VTPR`](@ref) equation of state. only works with activity models that define an excess residual gibbs energy function `Clapeyron.excess_g_res(model,P,T,z)` function (like [`UNIQUAC`](@ref) and [`UNIFAC`](@ref) models)

```
aᵢⱼ = √(aᵢaⱼ)(1-kᵢⱼ)
bᵢⱼ = ((bᵢ^(3/4) + bⱼ^(3/4))/2)^(4/3)
log(γʳ)ᵢ = lnγ_res(model.activity,V,T,z)
gᴱᵣₑₛ = ∑RTlog(γʳ)ᵢxᵢ
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄RT(∑[xᵢaᵢᵢαᵢ/(RTbᵢᵢ)] - gᴱᵣₑₛ/(0.53087RT))
```

## Model Construction Examples

```
# Note: this model was meant to be used exclusively with the VTPRUNIFAC activity model.

# Using the default database
mixing = VTPRRule(["water","carbon dioxide"]) #default: VTPRUNIFAC Activity Coefficient.
mixing = VTPRRule(["water","carbon dioxide"],activity = NRTL) #passing another Activity Coefficient Model
mixing = VTPRRule([("ethane",["CH3" => 2]),("butane",["CH2" => 2,"CH3" => 2])],activity = UNIFAC) #passing a GC Activity Coefficient Model.

# Passing a prebuilt model

act_model = NRTL(["water","ethanol"],userlocations = (a = [0.0 3.458; -0.801 0.0],b = [0.0 -586.1; 246.2 0.0], c = [0.0 0.3; 0.3 0.0]))
mixing = VTPRRule(["water","ethanol"],activity = act_model)

# Using user-provided parameters

# Passing files or folders
mixing = VTPRRule(["water","ethanol"]; activity = NRTL, activity_userlocations = ["path/to/my/db","nrtl_ge.csv"])

# Passing parameters directly
mixing = VTPRRule(["water","ethanol"];
                activity = NRTL,
                userlocations = (a = [0.0 3.458; -0.801 0.0],
                    b = [0.0 -586.1; 246.2 0.0],
                    c = [0.0 0.3; 0.3 0.0])
                )
```

## References

1. Ahlers, J., & Gmehling, J. (2001). Development of an universal group contribution equation of state. Fluid Phase Equilibria, 191(1–2), 177–188. [doi:10.1016/s0378-3812(01)00626-4](https://doi.org/10.1016/s0378-3812(01)00626-4)
