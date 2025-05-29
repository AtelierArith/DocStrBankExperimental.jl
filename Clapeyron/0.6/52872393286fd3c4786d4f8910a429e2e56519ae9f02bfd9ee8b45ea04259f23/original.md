```
vdW1fRule <: vdW1fRuleModel

vdW1fRule(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

None

## Description

van der Wals One-Fluid mixing rule for cubic parameters:

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
ā = ∑aᵢⱼxᵢxⱼ√(αᵢ(T)αⱼ(T))
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
mixing = vdW1fRule()
mixing = vdW1fRule("water")
mixing = vdW1fRule(["water","carbon dioxide"])
```
