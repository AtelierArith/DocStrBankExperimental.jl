```
threadfence()
```

A memory fence that acts as [`threadfence_block`](@ref) for all threads in the block of the calling thread and also ensures that no writes to all memory made by the calling thread after the call to `threadfence()` are observed by any thread in the device as occurring before any write to all memory made by the calling thread before the call to `threadfence()`.

Note that for this ordering guarantee to be true, the observing threads must truly observe the memory and not cached versions of it; this is requires the use of volatile loads and stores, which is not available from Julia right now.
