```
r = AdaptiveScalingWithinAdaptiveMetropolis(x0; kwargs)
r = AdaptiveScalingWithinAdaptiveMetropolis(x0, [acc_target, 
      [scale, [stepAM, [stepASM]]]])
```

AdaptiveScalingWithinAdaptiveMetropolis状態のコンストラクタ。

# 引数

  * `x0`: 初期状態ベクトル。

# キーワード引数

  * `acc_target`: 望ましい平均受け入れ率; デフォルトは `0.234`。
  * `scale`: 初期スケーリング; デフォルトは `2.38/sqrt(d)` で、`d` は次元。
  * `stepAM`: 共分散適応のためのステップサイズオブジェクト; デフォルトは `PolynomialStepSize(0.66)`。
  * `stepASM`: スケーリング適応のためのステップサイズオブジェクト; デフォルトは `PolynomialStepSize(0.66)`。

`s` が `RWMState` の場合、提案サンプルは `draw!(s, r)` を呼び出すことで引き出され、適応は `adapt!(r, s, α)` または `adapt_rb!(r, s, α)` で行われます。
