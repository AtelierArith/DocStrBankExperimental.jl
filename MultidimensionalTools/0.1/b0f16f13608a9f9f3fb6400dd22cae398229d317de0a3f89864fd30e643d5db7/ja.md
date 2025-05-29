```
n_adjacent_to(M::Array{T, N}, idx::Union{NTuple{N, Int}, CartesianIndex{N}}, adj_elem::T)
```

行列 M が与えられたとき、インデックス `idx` に隣接する要素のうち、ちょうど `adj_elem` である要素の数をカウントします。
