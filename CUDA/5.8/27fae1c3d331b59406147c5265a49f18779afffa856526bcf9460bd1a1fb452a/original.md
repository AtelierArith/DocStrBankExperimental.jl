```
launch(f::CuFunction; args...; blocks::CuDim=1, threads::CuDim=1,
       cooperative=false, shmem=0, stream=stream())
```

Low-level call to launch a CUDA function `f` on the GPU, using `blocks` and `threads` as respectively the grid and block configuration. Dynamic shared memory is allocated according to `shmem`, and the kernel is launched on stream `stream`.

Arguments to a kernel should either be bitstype, in which case they will be copied to the internal kernel parameter buffer, or a pointer to device memory.

This is a low-level call, prefer to use [`cudacall`](@ref) instead.
