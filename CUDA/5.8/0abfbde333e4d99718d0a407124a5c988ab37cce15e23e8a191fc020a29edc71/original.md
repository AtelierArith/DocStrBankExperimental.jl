```
cufunction(f, tt=Tuple{}; kwargs...)
```

Low-level interface to compile a function invocation for the currently-active GPU, returning a callable kernel object. For a higher-level interface, use [`@cuda`](@ref).

The following keyword arguments are supported:

  * `minthreads`: the required number of threads in a thread block
  * `maxthreads`: the maximum number of threads in a thread block
  * `blocks_per_sm`: a minimum number of thread blocks to be scheduled on a single multiprocessor
  * `maxregs`: the maximum number of registers to be allocated to a single thread (only supported on LLVM 4.0+)
  * `name`: override the name that the kernel will have in the generated code
  * `always_inline`: inline all function calls in the kernel
  * `fastmath`: use less precise square roots and flush denormals
  * `cap` and `ptx`: to override the compute capability and PTX version to compile for

The output of this function is automatically cached, i.e. you can simply call `cufunction` in a hot path without degrading performance. New code will be generated automatically, when when function changes, or when different types or keyword arguments are provided.
