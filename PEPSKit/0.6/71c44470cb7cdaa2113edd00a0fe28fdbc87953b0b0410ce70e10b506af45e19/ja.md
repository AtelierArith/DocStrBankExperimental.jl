```
su_iter(gate::LocalOperator, peps::InfiniteWeightPEPS, alg::SimpleUpdate; bipartite::Bool=false)
```

`peps`に最近接隣接の`gate`を適用して、シンプルアップデートの1ラウンドを実行します。
