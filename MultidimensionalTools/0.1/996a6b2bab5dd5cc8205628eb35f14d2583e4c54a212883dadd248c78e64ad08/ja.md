```
expanded_adjacencies(M::Array{T, N}, expand_by::T, idx::Union{NTuple{N, Int}, CartesianIndex{N}})
```

`expanded_adjacencies`は、行列Mのインデックスのすべての隣接要素を取得します。これは、行列が指定されたMを超えて単一の要素によって無限に拡張される場合です。 `reshape_as_required`も参照してください。
