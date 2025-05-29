```
launch_configuration(fun::CuFunction; shmem=0, max_threads=0)
```

Calculate a suggested launch configuration for kernel `fun` requiring `shmem` bytes of dynamic shared memory. Returns a tuple with a suggested amount of threads, and the minimal amount of blocks to reach maximal occupancy. Optionally, the maximum amount of threads can be constrained using `max_threads`.

In the case of a variable amount of shared memory, pass a callable object for `shmem` instead, taking a single integer representing the block size and returning the amount of dynamic shared memory for that configuration.
