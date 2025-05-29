```
r = AdaptiveScalingMetropolis(x0; kwargs)
r = AdaptiveScalingMetropolis(x0, [acc_target, [scale, [step]]])
r = AdaptiveScalingMetropolis(acc_target, scale, step)
```

AdaptiveScalingMetropolis状態のコンストラクタ。

# 引数

  * `x0`: 初期状態ベクトル（使用されません）。

# キーワード引数

  * `acc_target`: 望ましい平均受け入れ率；単変量の場合はデフォルト `0.44`、多変量の場合は `0.234`。
  * `scale`: 初期スケーリング；デフォルト `1.0`。
  * `step`: ステップサイズオブジェクト；デフォルト `PolynomialStepSize(0.66)`。

`s` が `RWMState` の場合、提案サンプルは `draw!(s, r)` を呼び出すことで引き出され、適応は `adapt!(r, s, α)` で行われます。
