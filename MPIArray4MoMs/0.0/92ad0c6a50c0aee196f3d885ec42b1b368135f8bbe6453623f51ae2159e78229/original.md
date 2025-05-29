```
PatternTransfer(reqsIndices::NTuple{3, Union{UnitRange{Int}, Vector{Int}}}, a::MPIArray{T, IA, 3}; comm = a.comm, rank = a.myrank, np = MPI.Comm_size(comm)) where {T, IA}
```

创建缓冲区 `PatternTransfer` 存储辐射函数、配置函数 Pattern 交换数据.
