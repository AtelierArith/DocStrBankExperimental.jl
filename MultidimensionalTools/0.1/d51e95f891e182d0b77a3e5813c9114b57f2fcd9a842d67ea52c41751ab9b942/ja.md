```
global_n_adjacent_to(M::Array{T, N},idx::Union{NTuple{N, Int}, CartesianIndex{N}}, adj_elem::T) where {N, T}
```

行列 M が与えられたとき、特定の要素をスキップしながら（`expanded_adjacencies` を参照）、インデックス `idx` に隣接する要素のうち、ちょうど `adj_elem` である要素の数をカウントします。
