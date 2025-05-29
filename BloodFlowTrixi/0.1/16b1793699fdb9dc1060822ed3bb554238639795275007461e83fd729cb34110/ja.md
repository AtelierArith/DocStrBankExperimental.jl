```
initial_condition_simple(x, t, eq::BloodFlowEquations2D; R0=2.0)
```

2D血流モデルの単純な初期条件を定義します。

### パラメータ

  * `x`: 位置ベクトル。
  * `t`: 初期時間。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。
  * `R0`: 初期半径（デフォルトは2.0）。

### 戻り値

`SVector`としての状態ベクトル。
