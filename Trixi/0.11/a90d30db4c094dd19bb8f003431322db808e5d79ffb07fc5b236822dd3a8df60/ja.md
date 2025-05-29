```
flux_hindenlang_gassner(u_ll, u_rr, orientation_or_normal_direction,
                        equations::IdealGlmMhdEquations3D)
```

エントロピー保存および運動エネルギー保存のためのHindenlangとGassner（2019）の二点フラックスで、[`flux_ranocha`](@ref)をMHD方程式に拡張しています。

## 参考文献

  * Florian Hindenlang, Gregor Gassner (2019) 第一原理から導出された理想MHD方程式のための新しいエントロピー保存二点フラックス。HONOM 2019: 高次数値法に関する欧州ワークショップで発表
  * Hendrik Ranocha (2018) 一般化された部分和演算子とハイパーボリックバランス法則の数値法のエントロピー安定性 [博士論文, TUブラウンシュバイク](https://cuvillier.de/en/shop/publications/7743)
  * Hendrik Ranocha (2020) 部分和演算子を用いたオイラー方程式のためのエントロピー保存および運動エネルギー保存の数値法 [ICOSAHOM 2018の議事録](https://doi.org/10.1007/978-3-030-39647-3_42)
