```
threadfence_system()
```

A memory fence that acts as [`threadfence_block`](@ref) for all threads in the block of the calling thread and also ensures that all writes to all memory made by the calling thread before the call to `threadfence_system()` are observed by all threads in the device, host threads, and all threads in peer devices as occurring before all writes to all memory made by the calling thread after the call to `threadfence_system()`.
