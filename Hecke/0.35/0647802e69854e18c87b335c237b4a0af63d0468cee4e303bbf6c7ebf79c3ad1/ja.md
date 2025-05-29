```
hermitian_lattice(E::NumField, gens::Vector ; gram = nothing) -> HermLat
```

ベクトルのリスト `gens` と次数 2 の数体 `E` が与えられたとき、`gens` の要素によって張られるエルミート空間内のエルミート格子を、グラム行列 `gram` と共に返します。

`gram` が指定されていない場合、周囲の空間のグラム行列は、`gens` の要素の長さに対してサイズが E の単位行列になります。

`gens` が空の場合、`gram` を指定する必要があり、関数はグラム行列 `gram` を持つ E 上のエルミート空間内のゼロ格子を返します。
