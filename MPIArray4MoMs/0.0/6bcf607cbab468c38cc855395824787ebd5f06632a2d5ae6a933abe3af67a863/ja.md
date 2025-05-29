```
mpiarray(T::DataType, Asize::Vararg{Int, N}; buffersize = 0, comm = MPI.COMM_WORLD, partition = (1, MPI.Comm_size(comm))) where {N}
```

サイズ `Asize` の MPI 配列を構築し、MPI `comm` でパーティションを分配します。
