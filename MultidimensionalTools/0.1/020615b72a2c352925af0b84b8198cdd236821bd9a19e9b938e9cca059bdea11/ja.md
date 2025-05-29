```
global_adjacencies(M::Matrix{T}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, ignored_elem::T)
```

`global_adjacencies_indices`を使用して、各グローバル隣接インデックスの要素を返します。この関数は主に`global_n_adjacent_to`で使用されます。
