```
IndicatorHennemannGassnerShallowWater(equations::AbstractEquations, basis;
                                      alpha_max=0.5,
                                      alpha_min=0.001,
                                      alpha_smooth=true,
                                      variable)
```

浅水方程の衝撃捕捉に使用される[`Trixi.IndicatorHennemannGassner`](@extref)インジケーターの修正版です。ブレンド係数の要素ごとの値が計算された後、要素が部分的に湿っているかどうかを確認する追加のチェックが行われます。この場合、部分的に湿った要素は、流れの状態の湿/乾の遷移に対して保証された良好なバランスを持つ純粋な有限体積スキームを使用するように設定されます。

[`Trixi.VolumeIntegralShockCapturingHG`](@extref)も参照してください。

## 参考文献

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
