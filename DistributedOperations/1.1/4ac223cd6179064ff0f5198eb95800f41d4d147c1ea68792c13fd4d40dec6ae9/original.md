```
x = ArrayFutures(T, n::NTuple{N,Int}[, pids=procs()])
```

Create `x::TypeFutures`, and where each proccess id (pid) in `pids` is assigned `zeros(T,n)`.

# Example

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
x = ArrayFutures(Float32, (10,20), procs())
localpart(x)
rmprocs(workers())
```
