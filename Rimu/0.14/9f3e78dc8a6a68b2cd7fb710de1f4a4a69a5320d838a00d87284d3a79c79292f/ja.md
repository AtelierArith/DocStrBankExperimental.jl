```
mpi_seed!(seed = rand(Random.RandomDevice(), UInt))
```

MPIに安全な方法で乱数生成器のシードを再設定します。シードが提供されると、`rand`からの乱数は決定論的なシーケンスに従います。

異なるMPIランクの乱数生成器の独立性は、`seed`に`hash(mpi_rank())`を追加することで達成されます。
