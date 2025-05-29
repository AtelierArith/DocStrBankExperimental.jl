```
getnumanodes(; threadpool = :default)
```

Returns the IDs (starting at zero) of the NUMA nodes corresponding to the CPU threads on which the Julia threads are currently running.

The keyword argument `threadpool` (default: `:default`) may be used to consider only those Julia threads that belong to a specific thread pool.
