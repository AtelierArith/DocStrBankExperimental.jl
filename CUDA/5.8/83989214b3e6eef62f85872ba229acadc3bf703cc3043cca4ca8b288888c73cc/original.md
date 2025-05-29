```
CuContext(dev::CuDevice, flags=CTX_SCHED_AUTO)
CuContext(f::Function, ...)
```

Create a CUDA context for device. A context on the GPU is analogous to a process on the CPU, with its own distinct address space and allocated resources. When a context is destroyed, the system cleans up the resources allocated to it.

When you are done using the context, call [`CUDA.unsafe_destroy!`](@ref) to mark it for deletion, or use do-block syntax with this constructor.
