```
bcast(x[, pids=procs()])
```

`x`を`pids`にブロードキャストします。

# 例

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
x = rand(10)
_x = bcast(x)
y = remotecall_fetch(localpart, workers()[1], _x)
y ≈ x  # true
rmprocs(workers())
```
