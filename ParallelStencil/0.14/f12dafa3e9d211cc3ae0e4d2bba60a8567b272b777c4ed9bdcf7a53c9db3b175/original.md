```
@ps_println(...)
```

Call a macro analogue to `Base.@println`, compatible with the package for parallelization selected with [`@init_parallel_stencil`](@ref) (Base.@println for Threads or Polyester and CUDA.@cuprintln for CUDA).
