```
UMRPR(components;
idealmodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

ユニバーサルミキシングルールペン・ロビンソン状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`MTTranslation`](@ref)
  * アルファモデル: [`MTAlpha`](@ref)
  * ミキシングルールモデル: [`UMRRule`](@ref) と [`UNIFAC`](@ref) 活動

## 参考文献

1. Voutsas, E., Magoulas, K., & Tassios, D. (2004). 対称および非対称システムに適用可能な立方体状態方程式のためのユニバーサルミキシングルール: ペン−ロビンソン状態方程式による結果。Industrial & Engineering Chemistry Research, 43(19), 6238–6246. [doi:10.1021/ie049580p](https://doi.org/10.1021/ie049580p)
