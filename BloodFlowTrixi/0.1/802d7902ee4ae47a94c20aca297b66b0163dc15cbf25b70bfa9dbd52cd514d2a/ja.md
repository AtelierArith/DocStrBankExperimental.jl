```
friction(u, x, eq::BloodFlowEquations2D)
```

2D血流モデルの摩擦項を計算します。

### パラメータ

  * `u`: 状態ベクトル。
  * `x`: 位置ベクトル。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

スカラーとしての摩擦項。
