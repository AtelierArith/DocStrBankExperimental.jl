```
NCCLBackend(comm = nothing, mpi_backend = nothing)
```

分散トレーニングのためのNCCLバックエンドを作成します。ユーザーはこの関数を直接使用すべきではありません。代わりに[`DistributedUtils.get_distributed_backend(NCCLBackend)`](@ref)を使用してください。
