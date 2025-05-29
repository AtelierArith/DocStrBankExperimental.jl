```
ContinuousNetworkHawkesProcess(baseline, impulses, weights, adjacency_matrix, network)
```

連続ネットワークハークスプロセス。

ネットワークハークスプロセスは、部分的に接続されたネットワークを許可します。バイナリの `adjacency_matrix` は、確率的な `network` モデルによって生成されたネットワーク接続を定義し、`adjacency_matrix[i, j]` はノード `i` からノード `j` への接続を表します。
