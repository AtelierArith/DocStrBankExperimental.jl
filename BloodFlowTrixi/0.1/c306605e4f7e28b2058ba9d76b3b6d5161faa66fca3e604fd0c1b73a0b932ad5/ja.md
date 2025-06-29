```
initial_condition_simple(x, t, eq::BloodFlowEquations1D; R0=2.0)
```

指定された初期半径 `R0` を持つ単純な初期条件を生成します。

### パラメータ

  * `x`: 位置ベクトル。
  * `t`: 時間スカラー。
  * `eq::BloodFlowEquations1D`: 血流モデルのインスタンス。
  * `R0`: 初期半径（デフォルト: `2.0`）。

### 戻り値

ゼロの初期面積摂動、ゼロの流量、一定の弾性係数、および `A_0 = \pi R_0^2` として計算された基準面積を持つ状態ベクトル。

この初期条件は、複雑な動力学なしで基本的なテストに適しています。
