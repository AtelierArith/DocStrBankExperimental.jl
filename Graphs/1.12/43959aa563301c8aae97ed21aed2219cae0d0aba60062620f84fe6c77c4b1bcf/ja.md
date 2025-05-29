```
non_backtracking_randomwalk(g, s, niter; rng=nothing, seed=nothing)
```

有向グラフ `g` で頂点 `s` から始めて、最大 `niter` ステップの間、バックトラッキングしないランダムウォークを実行します。訪れた頂点のベクトルを順番に返します。
