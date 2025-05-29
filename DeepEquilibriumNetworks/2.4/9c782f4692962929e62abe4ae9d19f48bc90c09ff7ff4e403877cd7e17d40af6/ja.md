```
DeepEquilibriumSolution(z_star, u₀, residual, jacobian_loss, nfe, solution)
```

DeepEquilibriumNetworkおよびその変種の解を保存します。

## フィールド

  * `z_star`: 定常状態またはmaxitersによって到達した値
  * `u0`: 初期条件
  * `residual`: $z^*$と$f(z^*, x)$の差
  * `jacobian_loss`: ヤコビ安定化損失（計算方法は個別のネットワークを参照）
  * `nfe`: 関数評価の数
  * `original`: 元の内部解
