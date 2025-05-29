```
short_vectors(L::ZZLat, [lb = 0], ub, [elem_type = ZZRingElem]; check::Bool = true)
                                   -> Vector{Tuple{Vector{elem_type}, QQFieldElem}}
```

すべてのタプル `(v, n)` を返します。ここで、$n = |v G v^t|$ が `lb <= n <= ub` を満たし、`G` は `L` のグラム行列であり、`v` はゼロでないとします。

ベクトルは符号まで計算されるため（したがって、`v` と `-v` のうちの1つだけが現れます）。

`L` が定義されていると仮定され、確認されます。

イテレーターバージョンについては、[`short_vectors_iterator`](@ref) を参照してください。
