```
x = TypeFutures(y::T, pids)
```

Construct a `x::TypeFutures` from `y::T` on the master process.  This is useful for creating `x` prior to the construction of a cluster.  Subsequently, `x` can be used to broadcast `y` to workers.

# Example

```
using Distributed, DistributedOperations
y = (x=rand(2),y=rand(2))
x = TypeFutures(y)
addprocs(2)
@everywhere using DistributedOperations
bcast!(x, workers())
```
