```
local_join!(graph; kwargs...)
```

グラフ内の各頂点 `v` の近傍 `N[v]` でローカルジョインを実行します。頂点 `v` とその隣接点 `N[v]` が与えられたとき、各ペア `p, q ∈ N[v]` に対して類似度 `graph.metric(p, q)` を計算し、`N[q]` と `N[p]` を更新します。

これは `graph` をインプレースで変更し、ローカルジョイン中に行われた隣接点の更新数を示す非負整数を返します。
