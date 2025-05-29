```
KayRule <: KayRuleModel

KayRule(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

None

## Description

Kay mixing rule for cubic parameters:

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
ā = b̄*(∑[aᵢⱼxᵢxⱼ√(αᵢ(T)αⱼ(T))/bᵢⱼ])^2
b̄ = (∑∛(bᵢⱼ)xᵢxⱼ)^3
c̄ = ∑cᵢxᵢ
```

## Model Construction Examples

```
# Because this model does not have parameters, all those constructors are equivalent:
mixing = KayRule()
mixing = KayRule("water")
mixing = KayRule(["water","carbon dioxide"])
```
