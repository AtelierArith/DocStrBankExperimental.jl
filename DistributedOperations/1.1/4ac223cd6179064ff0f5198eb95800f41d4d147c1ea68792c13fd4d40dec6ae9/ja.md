```
x = ArrayFutures(T, n::NTuple{N,Int}[, pids=procs()])
```

`x::TypeFutures`を作成し、`pids`の各プロセスID（pid）に`zeros(T,n)`が割り当てられます。

# 例

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
x = ArrayFutures(Float32, (10,20), procs())
localpart(x)
rmprocs(workers())
```
