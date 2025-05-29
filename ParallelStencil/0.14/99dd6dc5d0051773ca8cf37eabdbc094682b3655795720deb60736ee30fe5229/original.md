```
@init_parallel_stencil(package, numbertype, ndims)
@init_parallel_stencil(package, numbertype, ndims, inbounds=...)
@init_parallel_stencil(package=..., ndims=..., inbounds=...)
```

Initialize the package ParallelStencil, giving access to its main functionality. Creates a module `Data` in the module where `@init_parallel_stencil` is called from. The module `Data` contains the types as `Data.Number`, `Data.Array` and `Data.CellArray` (type `?Data` *after* calling `@init_parallel_stencil` to see the full description of the module).

# Arguments

  * `package::Module`: the package used for parallelization (CUDA, AMDGPU or Metal for GPU, or Threads or Polyester for CPU).
  * `numbertype::DataType`: the type of numbers used by @zeros, @ones, @rand and @fill and in all array types of module `Data` (e.g. Float32 or Float64). It is contained in `Data.Number` after @init*parallel*stencil. The `numbertype` can be omitted if the other arguments are given as keyword arguments (in that case, the `numbertype` will have to be given explicitly when using the types provided by the module `Data`).
  * `ndims::Integer`: the number of dimensions used for the stencil computations in the kernels: 1, 2 or 3 (overwritable in each kernel definition).
  * `inbounds::Bool=false`: whether to apply `@inbounds` to the kernels by default (overwritable in each kernel definition).

See also: [`Data`](@ref)
