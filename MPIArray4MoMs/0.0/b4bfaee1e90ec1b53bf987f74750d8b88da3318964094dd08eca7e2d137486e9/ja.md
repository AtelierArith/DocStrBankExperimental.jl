```
ArrayTransfer(reqsIndices::NTuple{N, I}, a::MPIArray{T, IA, N}; comm = a.comm, rank = a.myrank, np = MPI.Comm_size(comm)) where {N, I, T, IA}
```

`reqsIndices`と共に`a`のデータを同期するためのバッファを作成します。
