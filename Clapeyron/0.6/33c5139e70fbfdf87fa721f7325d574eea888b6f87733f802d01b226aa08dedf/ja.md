```
QCPR(components;
    idealmodel = BasicIdeal,
    userlocations = String[], 
    ideal_userlocations = String[],
    alpha_userlocations = String[],
    mixing_userlocations = String[],
    activity_userlocations = String[],
    translation_userlocations = String[],
    reference_state = nothing,
    verbose = false)
```

量子補正されたペン・ロビンソン状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`ConstantTranslation`](@ref)
  * アルファモデル: [`TwuAlpha`](@ref)
  * 混合則モデル: [`QCPRRule`](@ref)

## 参考文献

1. Aasen, A., Hammer, M., Lasala, S., Jaubert, J.-N., & Wilhelmsen, Ø. (2020). Accurate quantum-corrected cubic equations of state for helium, neon, hydrogen, deuterium and their mixtures. Fluid Phase Equilibria, 524(112790), 112790. [doi:10.1016/j.fluid.2020.112790](https://doi.org/10.1016/j.fluid.2020.112790)
