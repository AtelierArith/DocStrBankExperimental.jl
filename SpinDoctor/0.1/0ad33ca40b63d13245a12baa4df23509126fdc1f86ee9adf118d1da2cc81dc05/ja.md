```
compute_signal(M, ξ)
```

磁化 `ξ` から信号を計算し、積分のために質量行列 `M` を使用します。

メッシュ `mesh` と区画質量行列のベクトル `M_cmpts` が与えられた場合、区画信号のベクトルは `compute_signal.(M_cmpts, split_field(mesh, ξ))` によって得られます。
