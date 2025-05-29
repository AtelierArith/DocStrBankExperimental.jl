```
PatternTransfer(reqsIndices::NTuple{3, Union{UnitRange{Int}, Vector{Int}}}, a::MPIArray{T, IA, 3}; comm = a.comm, rank = a.myrank, np = MPI.Comm_size(comm)) where {T, IA}
```

作成バッファ `PatternTransfer` は放射関数、設定関数 Pattern のデータを交換します。
