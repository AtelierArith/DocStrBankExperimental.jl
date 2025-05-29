```
global_adjacencies(M::Matrix{T}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, ignored_elem::T)
```

指定されたインデックスからの行列 `M` の任意の位置における「グローバルに」隣接するインデックスを、特定の隣接要素を無視して（つまり、それらをスキップして）返します。
