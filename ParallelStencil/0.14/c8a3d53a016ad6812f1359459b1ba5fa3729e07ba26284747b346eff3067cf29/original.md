```
@sync_threads()
```

Synchronize the threads of the block: wait until all threads in the block have reached this point and all global and shared memory accesses made by these threads prior to the `sync_threads()` call are visible to all threads in the block.
