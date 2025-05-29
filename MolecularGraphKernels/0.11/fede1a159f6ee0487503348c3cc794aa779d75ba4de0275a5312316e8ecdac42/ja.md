```
kernel_score = random_walk(adj_mat; l=n)
kernel_score = random_walk(g₁xg₂; l=n)
kernel_score = random_walk(g₁, g₂; l=n)
```

2つのグラフの類似度スコアを、直接積グラフを介して `l`-長さのランダムウォークグラフカーネル（random_walk）を適用することによって返します。
