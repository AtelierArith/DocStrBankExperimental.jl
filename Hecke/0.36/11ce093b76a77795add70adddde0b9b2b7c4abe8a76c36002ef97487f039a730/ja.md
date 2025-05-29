```
quadratic_lattice(K::Field ; gram::MatElem) -> Union{ZZLat, QuadLat}
```

行列 `gram` と体 `K` が与えられたとき、Gram 行列 `gram` を持つ体 `K` 上の二次空間内の自由二次格子を返します。

もし $K = \mathbb{Q}$ であれば、出力される格子は `ZZLat` 型であり、環 $\mathbb{Z}$ 上の格子として見なされます。
