```
remoterank2indices(remoteranks, indices, rank2ghostindices::Dict{Int, T}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{T}
```

リモートランクとデータ内の相対インデックスを取得します。
