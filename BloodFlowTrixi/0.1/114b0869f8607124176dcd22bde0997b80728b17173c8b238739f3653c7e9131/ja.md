```
source_term_simple(u, x, t, eq::BloodFlowEquations2D)
```

2D血流モデルの単純なソース項を計算します。摩擦および曲率効果を含みます。

### パラメータ

  * `u`: 状態ベクトル。
  * `x`: 位置ベクトル。
  * `t`: 時間値。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

`SVector`としてのソース項。
