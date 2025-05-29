```
x = TypeFutures(y::T, pids)
```

マスタープロセス上で `y::T` から `x::TypeFutures` を構築します。これは、クラスターの構築前に `x` を作成するのに便利です。その後、`x` を使用して `y` をワーカーにブロードキャストできます。

# 例

```
using Distributed, DistributedOperations
y = (x=rand(2),y=rand(2))
x = TypeFutures(y)
addprocs(2)
@everywhere using DistributedOperations
bcast!(x, workers())
```
