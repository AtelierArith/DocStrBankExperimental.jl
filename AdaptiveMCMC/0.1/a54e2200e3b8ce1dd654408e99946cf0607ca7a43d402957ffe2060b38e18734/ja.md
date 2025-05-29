```
r = RobustAdaptiveMetropolis(x0; kwargs)
r = RobustAdaptiveMetropolis(x0, [acc_target, [step]])
```

RobustAdaptiveMetropolis状態のコンストラクタ。

# 引数

  * `x0`: 初期状態ベクトル

# キーワード引数

  * `acc_target`: 望ましい平均受け入れ率; デフォルトは `0.234`。
  * `step`: ステップサイズオブジェクト; デフォルトは `RAMStepSize(0.66,d)` で、`d` は状態次元。
  * `S_init`: 初期提案形状のコレスキー因子; デフォルトは `identity_cholesky(x0)`

`s` が `RWMState` の場合、提案サンプルは `draw!(s, r)` を呼び出すことで引き出され、適応は `adapt!(r, s, α)` で行われます。
