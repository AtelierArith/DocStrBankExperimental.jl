```
grank2indices(ghostranks, ghostindices::NTuple{N, Union{UnitRange{T}, Vector{T}}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T,  T2}
```

ゴーストランクのゴーストデータのグローバルインデックスを取得します。
