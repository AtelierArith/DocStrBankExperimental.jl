```
KMR(N, payoff_array, epsilon)
```

新しいKMRインスタンスを作成します。

# 引数

  * `N::Integer` : プレイヤーの数。
  * `payoff_array::Matrix` : 各プレイヤーのためのペイオフ配列。
  * `epsilon::Float64` : 戦略変更の確率。

# 戻り値

  * `::KMR` : Kandori Mailath Robモデル。
