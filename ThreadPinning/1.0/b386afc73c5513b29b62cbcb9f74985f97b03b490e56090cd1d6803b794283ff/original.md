```
getcpuids(; threadpool = :default)
```

Returns the IDs of the CPU-threads on which the Julia threads are currently running on.

The keyword argument `threadpool` (default: `:default`) may be used to specify a specific thread pool.
