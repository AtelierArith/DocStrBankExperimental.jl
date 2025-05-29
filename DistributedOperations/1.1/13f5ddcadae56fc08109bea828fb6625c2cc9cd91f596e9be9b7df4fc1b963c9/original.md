```
bcast!(x::TypeFutures, pids)
```

Broadcast an existing `x::TypeFutures` to `pids`.  This is useful for elastic computing where the cluster may grow after the construction and broadcast of `x::TypeFuture`.
