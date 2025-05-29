```
AdaptiveTraining(pde_weights, bcs_weights)
```

損失関数の適応重み。ここで `pde_weights` と `bcs_weights` は `(phi, x, θ)` を引数に取り、点ごとの重みを返す関数です。`bcs_weights` は実数である可能性がありますが、同じ数値を返す関数に変換されます。
