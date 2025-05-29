```
short_vectors_iterator(L::ZZLat, [lb = 0], ub,
                       [elem_type = ZZRingElem]; check::Bool = true)
                                -> Tuple{Vector{elem_type}, QQFieldElem} (iterator)
```

すべてのタプル `(v, n)` のイテレータを返します。ここで、$n = |v G v^t|$ が `lb <= n <= ub` を満たし、`G` は `L` のグラム行列であり、`v` はゼロでないとします。

ベクトルは符号まで計算されるため（したがって、`v` と `-v` のうちの1つだけが現れます）。

`L` が定義されていると仮定され、確認されます。

[`short_vectors`](@ref) も参照してください。
