```
VTPR(components;
idealmodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[]
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

体積変換されたペン・ロビンソン状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`RackettTranslation`](@ref)
  * アルファモデル: [`TwuAlpha`](@ref)
  * 混合則モデル: [`VTPRRule`](@ref) と [`VTPRUNIFAC`](@ref) 活動

## 参考文献

1. Ahlers, J., & Gmehling, J. (2001). Development of an universal group contribution equation of state. Fluid Phase Equilibria, 191(1–2), 177–188. [doi:10.1016/s0378-3812(01)00626-4](https://doi.org/10.1016/s0378-3812(01)00626-4)
