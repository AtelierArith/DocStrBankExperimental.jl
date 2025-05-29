```
expanded_n_adjacent_to(M::Array{T, N}, expand_by::T, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, adj_elem::T)
```

行列 M が与えられたとき、インデックス `idx` に隣接する要素のうち、ちょうど `adj_elem` である要素の数をカウントし、必要に応じて行列を拡張します（`expanded_adjacencies` を参照）。
