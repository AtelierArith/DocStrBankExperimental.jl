```
@rand(args...)
@rand(args..., <keyword arguments>)
```

Call `rand(eltype, args...)`, where `eltype` is by default the `numbertype` selected with [`@init_parallel_stencil`](@ref) and the function `rand` is chosen/implemented to be compatible with the package for parallelization selected with [`@init_parallel_stencil`](@ref).

!!! note "Advanced"
    The `eltype` can be explicitly passed as keyword argument in order to be used instead of the default `numbertype` chosen with [`@init_parallel_stencil`](@ref). If no default `numbertype` was chosen [`@init_parallel_stencil`](@ref), then the keyword argument `eltype` is mandatory. This needs to be used with care to ensure that no datatype conversions occur in performance critical computations.


# Keyword arguments

  * `eltype::DataType`: the type of the elements, which can be numbers, indices, booleans or enums.
  * `celldims::Integer|NTuple{N,Integer}=1`: the dimensions of each array cell. Each cell can contain a single value (default) or an N-dimensional array of the specified dimensions.

!!! note "Advanced"
      * `celltype::DataType`: the type of each array cell; it must be generated with the macro `@CellType`. The keyword argument `celltype` is incompatible with the other keyword arguments: if any of them is set, then the `celltype` is automatically defined. The `celltype` needs only to be specified to use named cell fields. Note that values can always be addressed with array indices, even when cell field names are defined.
      * `blocklength::Integer`: refers to the amount of values of a same `Cell` field that are stored contigously (`blocklength=1` means array of struct like storage; `blocklength=prod(dims)` means array struct of array like storage; `blocklength=0` is an alias for `blocklength=prod(dims)`, enabling better peformance thanks to more specialized dispatch). By default, `blocklength` is automatically set to `0` if a GPU package was chosen with [`@init_parallel_stencil`](@ref) and to `1` if a CPU package was chosen. Furthermore, the argument `blocklength` is only of effect if either `celldims` or `celltype` is set, else it is ignored.


See also: [`@zeros`](@ref), [`@ones`](@ref), [`@falses`](@ref), [`@trues`](@ref), [`@fill`](@ref), [`@CellType`](@ref)
