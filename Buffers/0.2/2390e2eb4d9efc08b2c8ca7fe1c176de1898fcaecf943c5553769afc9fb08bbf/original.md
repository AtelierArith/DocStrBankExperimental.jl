```
repair!(buf::AbstractThreadsBuffer)
```

Repair ThreadsBuffer `buf` by releasing all buffers and resetting the pool.

This function should be used after the threaded loop  if the buffers were not released properly.
