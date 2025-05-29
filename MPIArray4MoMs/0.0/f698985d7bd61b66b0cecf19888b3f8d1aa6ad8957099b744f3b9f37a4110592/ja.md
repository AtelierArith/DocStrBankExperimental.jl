```
grank2gdataSize(ghostranks, ghostindices::NTuple{N, Union{UnitRange{Int}, Vector{Int}}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T2}
```

ゴーストデータのサイズを取得します。
