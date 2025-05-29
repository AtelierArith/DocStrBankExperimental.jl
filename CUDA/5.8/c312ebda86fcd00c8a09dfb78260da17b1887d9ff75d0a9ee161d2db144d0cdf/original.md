```
threadfence_block()
```

A memory fence that ensures that:

  * All writes to all memory made by the calling thread before the call to `threadfence_block()` are observed by all threads in the block of the calling thread as occurring before all writes to all memory made by the calling thread after the call to `threadfence_block()`
  * All reads from all memory made by the calling thread before the call to `threadfence_block()` are ordered before all reads from all memory made by the calling thread after the call to `threadfence_block()`.
