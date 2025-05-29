```
occupancy(fun::CuFunction, threads; shmem=0)
```

Calculate the theoretical occupancy of launching `threads` threads of a kernel `fun` requiring `shmem` bytes of dynamic shared memory.
