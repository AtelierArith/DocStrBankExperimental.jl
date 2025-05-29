```
quadratic_lattice(K::Field, basis::MatElem ; gram = nothing,
                                             check::Bool = true)
                                                      -> Union{ZZLat, QuadLat}
```

行列 `basis` と体 `K` が与えられたとき、`basis` の行によって張られる二次格子を、グラム行列 `gram` を用いて `K` 上の二次空間内で返します。

`gram` が指定されていない場合、周囲の空間のグラム行列は、`basis` の列数のサイズを持つ `K` 上の単位行列になります。

デフォルトでは、`basis` がフルランクであることが確認されます。このテストは、`check` を false に設定することで無効にできます。

もし $K = \mathbb{Q}$ であれば、出力される格子は `ZZLat` 型であり、$\mathbb{Z}$ 上の格子として見なされます。
