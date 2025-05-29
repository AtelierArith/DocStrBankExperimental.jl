```
CosAnneal(l0, l1, period, restart = true)
CosAnneal(; l0, l1, period, restart = true)
```

コサインアニーリングスケジュール（「SGDR: Stochastic Gradient Descent with Warm Restarts」を参照）出力は次のようになります。

```text
t̂ = restart ? mod(t - 1, period) : (t - 1)
abs(l0 - l1) * (1 + cos(π * t̂ / period)) / 2 + min(l0, l1)
```

このスケジュールは、機械学習文献では「コサインアニーリング（ウォームリスタート付き）」とも呼ばれています。

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期
  * `restart::Bool`: ウォームリスタートを使用する
