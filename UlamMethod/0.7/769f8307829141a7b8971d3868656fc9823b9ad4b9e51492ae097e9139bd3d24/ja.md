```
struct Trajectories{Dim}
```

次元 `Dim` の軌道データのコンテナ。

### フィールド

  * `x0`: 初期座標で、サイズ `Dim` x `n_traj` の行列である必要があります。
  * `xT`: 最終座標で、サイズ `Dim` x `n_traj` の行列である必要があります。

### コンストラクタ

```
Trajectories(x0, xT)
```

データから直接 `Trajectories` を構築します。

```
Trajectories(dim, n_traj; corners = nothing, mu_sigma = nothing)
```

テスト用に次元 `dim` の `n_traj` のランダムな `Trajectories` を構築します。

`x0` は、`corners = ((xmin, ymin, zmin, ...), (xmax, ymax, zmax, ...))` で定義されたボックスの内部に位置し、提供されない場合は単位ボックスがデフォルトとなります。

`xT` は、各次元に沿った正規分布によって `x0` からずれたもので、平均と分散は `mu_sigma = [(mu1, sigma1), (mu2, sigma2), ...]` で定義されます。提供されない場合は、デフォルトで `mu = 1.0`、`sigma = 1.0` となります。
