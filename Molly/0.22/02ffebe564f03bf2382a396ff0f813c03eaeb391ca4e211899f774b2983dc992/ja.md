```
ReplicaExchangeLogger(n_replicas)
ReplicaExchangeLogger(T, n_replicas)
```

レプリカ交換シミュレーションにおける交換を記録するロガーです。

記録される量には、交換試行の数（`n_attempts`）、成功した交換の数（`n_exchanges`）、交換されたレプリカのインデックス（`indices`）、交換ステップ（`steps`）、および交換のためのメトロポリス率の引数であるΔの値（`deltas`）が含まれます。
