```
shortest_vectors(L::ZZLat, [elem_type = ZZRingElem]; check::Bool = true)
                                           -> QQFieldElem, Vector{elem_type}, QQFieldElem}
```

絶対値が最小の非ゼロベクトルのリストを返します。ベクトルは符号まで計算されるため（したがって `v` と `-v` のうちの1つのみが表示されます）。

`L` が確定的であると仮定され、確認されます。

詳細は [`minimum`](@ref) を参照してください。
