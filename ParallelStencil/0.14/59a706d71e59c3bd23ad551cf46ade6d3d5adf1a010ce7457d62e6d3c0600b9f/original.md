```
@sharedMem(T, dims, offset::Integer=0)
```

Create an array that is *shared* between the threads of a block (i.e. accessible only by the threads of a same block), with element type `T` and size specified by `dims`.  When multiple shared memory arrays are created within a kernel, then all arrays except for the first one typically need to define the `offset` to the base shared memory pointer in bytes (note that the CPU and AMDGPU implementation do not require the `offset` and will simply ignore it when present).

!!! note
    The amount of shared memory needs to be specified when launching the kernel (keyword argument `shmem`).

