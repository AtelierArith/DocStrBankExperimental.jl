```
function PSRK(components;
idealmodel = BasicIdeal,
alpha = SoaveAlpha,
mixing = PSRKRule,
activity = PSRKUNIFAC,
translation = PenelouxTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 説明

予測的ソーヴェ-レドリッヒ-クワンゴ状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`NoTranslation`](@ref)
  * アルファモデル: [`SoaveAlpha`](@ref)
  * 混合則モデル: [`PSRKRule`](@ref) と [`PSRKUNIFAC`](@ref) 活動モデル

## 参考文献

1. Horstmann, S., Jabłoniec, A., Krafczyk, J., Fischer, K., & Gmehling, J. (2005). PSRKグループ寄与状態方程式: 包括的な改訂と拡張IV、1000成分のための臨界定数とα関数パラメータを含む。流体相平衡, 227(2), 157–164. [doi:10.1016/j.fluid.2004.11.002](https://doi.org/10.1016/j.fluid.2004.11.002)
