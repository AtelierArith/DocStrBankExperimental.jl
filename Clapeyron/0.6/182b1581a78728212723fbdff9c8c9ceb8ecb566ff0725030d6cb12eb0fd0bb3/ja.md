```
cPR(components::Vector{String};
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

一貫したペン・ロビンソン状態方程式。以下のモデルを使用します：

  * 翻訳モデル: [`NoTranslation`](@ref)
  * アルファモデル: [`TwuAlpha`](@ref)
  * 混合則モデル: [`vdW1fRule`](@ref)

## 参考文献

1. Bell, I. H., Satyro, M., & Lemmon, E. W. (2018). 一貫したtwuパラメータを2500以上の純流体に対して、批判的に評価された実験データから得た。化学工学データジャーナル, 63(7), 2402–2409. [doi:10.1021/acs.jced.7b00967](https://doi.org/10.1021/acs.jced.7b00967)
