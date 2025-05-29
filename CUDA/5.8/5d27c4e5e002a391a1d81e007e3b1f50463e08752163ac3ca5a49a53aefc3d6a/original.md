```
active_blocks(fun::CuFunction, threads; shmem=0)
```

Calculate the maximum number of active blocks per multiprocessor when running `threads` threads of a kernel `fun` requiring `shmem` bytes of dynamic shared memory.
