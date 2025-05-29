```
@ps_show(...)
```

Call a macro analogue to `Base.@show`, compatible with the package for parallelization selected with [`@init_parallel_stencil`](@ref) (Base.@show for Threads or Polyester and CUDA.@cushow for CUDA).
