```
QCPRRule <: MHV2RuleModel

QCPRRule(components;
activity = Wilson,
userlocations = String[],
activity_userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 入力モデル

  * `activity`: アクティビティモデル

## 説明

量子補正混合則、[`QCPR`](@ref) EoSによって使用されます：

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)(bqᵢ + bqⱼ)/2
bqᵢ = bᵢβᵢ(T)
βᵢ(T) = (1 + Aᵢ/(T + Bᵢ))^3 / (1 + Aᵢ/(Tcᵢ + Bᵢ))^3
ā = ∑aᵢⱼxᵢxⱼ√(αᵢ(T)αⱼ(T))
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
```

## 参考文献

1. Aasen, A., Hammer, M., Lasala, S., Jaubert, J.-N., & Wilhelmsen, Ø. (2020). Accurate quantum-corrected cubic equations of state for helium, neon, hydrogen, deuterium and their mixtures. Fluid Phase Equilibria, 524(112790), 112790. [doi:10.1016/j.fluid.2020.112790](https://doi.org/10.1016/j.fluid.2020.112790)
