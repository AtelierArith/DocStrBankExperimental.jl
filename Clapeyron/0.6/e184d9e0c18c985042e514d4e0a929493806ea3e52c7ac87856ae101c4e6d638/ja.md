```
PPR78Rule <: PPR78RuleModel

PPR78Rule(components;
userlocations = String[],
group_userlocations = String[]
verbose::Bool=false)
```

## 入力パラメータ

  * `A`: ペアパラメータ (`Float64`) - フィッティングパラメータ `[K]`
  * `B`: ペアパラメータ (`Float64`) - フィッティングパラメータ `[K]`

## 説明

PPR78混合則、E-PPR78グループパラメータを使用します。[`EPPR78`](@ref) EoSのデフォルトです。

```
aᵢⱼ = √(aᵢaⱼ)
bᵢⱼ = (bᵢ +bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄(∑[xᵢaᵢαᵢ/(bᵢᵢ)] - ∑xᵢxⱼbᵢbⱼEᵢⱼ/2b̄)
Eᵢⱼ = ∑(z̄ᵢₖ - z̄ⱼₖ)(z̄ᵢₗ - z̄ⱼₗ) × Aₖₗ × (298.15/T)^(Aₖₗ/Bₖₗ - 1)
```

## 参考文献

1. Jaubert, J.-N., Privat, R., & Mutelet, F. (2010). PPR78アプローチを用いた合成石油流体の相平衡の予測。AIChEジャーナル。アメリカ化学工学会、56(12), 3225–3235. [doi:10.1002/aic.12232](https://doi.org/10.1002/aic.12232)
2. Jaubert, J.-N., Qian, J.-W., Lasala, S., & Privat, R. (2022). 状態方程式のパラメータ化における混合データのエンタルピーと比熱を含めることの印象的な影響。E-PPR78（強化予測ペン・ロビンソン78）モデルの開発への応用。流体相平衡、(113456), 113456. [doi:10.1016/j.fluid.2022.113456](https://doi.org/10.1016/j.fluid.2022.113456)
