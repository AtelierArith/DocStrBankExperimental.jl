```
MPIBackend(comm = nothing)
```

分散トレーニングのためのMPIバックエンドを作成します。ユーザーはこの関数を直接使用すべきではありません。代わりに [`DistributedUtils.get_distributed_backend(MPIBackend)`](@ref) を使用してください。
