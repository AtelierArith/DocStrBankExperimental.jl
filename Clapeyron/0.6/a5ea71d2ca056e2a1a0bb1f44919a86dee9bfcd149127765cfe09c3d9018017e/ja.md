```
EPPR78(components_or_groups;
idealmodel = BasicIdeal,
alpha = PR78Alpha,
mixing = PPR78Rule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

強化予測ペン・ロビンソン状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`NoTranslation`](@ref)
  * アルファモデル: [`PR78Alpha`](@ref)
  * 混合則モデル: [`PPR78Rule`](@ref)

## 参考文献

1. Jaubert, J.-N., Privat, R., & Mutelet, F. (2010). PPR78アプローチを用いた合成石油流体の相平衡の予測。AIChEジャーナル。アメリカ化学工学会、56(12), 3225–3235. [doi:10.1002/aic.12232](https://doi.org/10.1002/aic.12232)
2. Jaubert, J.-N., Qian, J.-W., Lasala, S., & Privat, R. (2022). 状態方程式のパラメータ化における混合データのエンタルピーと比熱容量を含めることの印象的な影響。E-PPR78（強化予測ペン・ロビンソン-78）モデルの開発への応用。流体相平衡, (113456), 113456. [doi:10.1016/j.fluid.2022.113456](https://doi.org/10.1016/j.fluid.2022.113456)
