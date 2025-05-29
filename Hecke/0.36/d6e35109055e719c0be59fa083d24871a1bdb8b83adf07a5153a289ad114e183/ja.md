```
quadratic_lattice(K::Field, gens::Vector ; gram = nothing) -> Union{ZZLat, QuadLat}
```

ベクトルのリスト `gens` とフィールド `K` が与えられたとき、`gens` の要素によって張られた二次格子を、グラム行列 `gram` を用いて `K` 上の二次空間内で返します。

`gram` が指定されていない場合、周囲の空間のグラム行列は、`gens` の要素の長さに対して `K` 上の単位行列になります。

`gens` が空の場合、`gram` を指定する必要があり、関数はグラム行列 `gram` を持つ `K` 上の二次空間内のゼロ格子を返します。

もし $K = \mathbb{Q}$ であれば、出力される格子は `ZZLat` 型であり、$\mathbb{Z}$ 上の格子として見なされます。
