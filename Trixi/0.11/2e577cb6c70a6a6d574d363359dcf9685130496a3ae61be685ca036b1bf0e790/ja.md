```
flux_hindenlang_gassner(u_ll, u_rr, orientation_or_normal_direction,
                        equations::IdealGlmMhdMulticomponentEquations2D)
```

Hindenlang (2019) のエントロピー保存および運動エネルギー保存の二点フラックスの適応、[`flux_ranocha`](@ref) を MHD 方程式に拡張します。

## 参考文献

  * Florian Hindenlang, Gregor Gassner (2019) 第一原理から導出された理想 MHD 方程式のための新しいエントロピー保存二点フラックス。HONOM 2019: 高次数値法に関する欧州ワークショップで発表
  * Hendrik Ranocha (2018) 一般化された部分和演算子とハイパーボリックバランス法則の数値法のエントロピー安定性 [博士論文, TU ブラウンシュヴァイク](https://cuvillier.de/en/shop/publications/7743)
  * Hendrik Ranocha (2020) 部分和演算子を用いたオイラー方程式のためのエントロピー保存および運動エネルギー保存の数値法 [ICOSAHOM 2018 論文集](https://doi.org/10.1007/978-3-030-39647-3_42)
