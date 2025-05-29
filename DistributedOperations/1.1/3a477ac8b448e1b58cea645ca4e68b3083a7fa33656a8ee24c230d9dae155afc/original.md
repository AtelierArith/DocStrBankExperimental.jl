```
x = ArrayFutures(x::Array[, pids=procs()])
```

Create `x::TypeFutures`, and where `myid()` is assigned `x`, and all other processes are assigned `zeros(eltype(x), size(x))`.
