```
random_walk_pe(g, walk_length)
```

与えられたグラフ `g` とウォークの長さ `walk_length` に基づいて、論文 [Graph Neural Networks with Learnable Structural and Positional Representations](https://arxiv.org/abs/2110.07875) からのランダムウォーク位置エンコーディングを、サイズ `(walk_length, g.num_nodes)` の行列として返します。
