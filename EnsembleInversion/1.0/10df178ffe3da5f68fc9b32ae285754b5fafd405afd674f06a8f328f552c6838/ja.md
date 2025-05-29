```
EKI(G::Function, x_ensemble::Matrix{T}, y_target=zero(T), alpha=T(1e-8)*I)
```

モデル `y = G(x)` を次のように解きます：

```
`G` : 次元 `D` のベクトル `x` を受け取り、サイズ `K` の予測観測ベクトル `y` を返すモデル

`x_ensemble` : サイズ D-by-N の行列、候補解の初期集団

`y_target` : サイズ K のベクトル、ターゲットモデル観測を表す

`alpha` : 正則化として作用するサイズ K-by-K の共分散行列
```

予測誤差が低い新しい `x_ensemble` 行列を返します。
