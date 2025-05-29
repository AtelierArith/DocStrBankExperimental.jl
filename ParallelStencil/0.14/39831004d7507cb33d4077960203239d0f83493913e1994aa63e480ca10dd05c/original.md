```
@trues(args...)
@trues(args..., <keyword arguments>)
```

Call `trues(args...)`, where the function `trues` is chosen to be compatible with the package for parallelization selected with [`@init_parallel_stencil`](@ref).

# Keyword arguments

  * `celldims::Integer|NTuple{N,Integer}=1`: the dimensions of each array cell. Each cell can contain a single value (default) or an N-dimensional array of the specified dimensions.

!!! note "Advanced"
      * `blocklength::Integer`: refers to the amount of values of a same `Cell` field that are stored contigously (`blocklength=1` means array of struct like storage; `blocklength=prod(dims)` means array struct of array like storage; `blocklength=0` is an alias for `blocklength=prod(dims)`, enabling better peformance thanks to more specialized dispatch). By default, `blocklength` is automatically set to `0` if a GPU package was chosen with [`@init_parallel_stencil`](@ref) and to `1` if a CPU package was chosen. Furthermore, the argument `blocklength` is only of effect if either `celldims` or `celltype` is set, else it is ignored.


See also: [`@zeros`](@ref), [`@ones`](@ref), [`@rand`](@ref), [`@falses`](@ref), [`@fill`](@ref), [`@CellType`](@ref)
