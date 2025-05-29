```
@fill!(A, x)
@fill!(A, x)
```

Call `fill!(A, x)`, where the function `fill` is chosen/implemented to be compatible with the package for parallelization selected with [`@init_parallel_stencil`](@ref).

# Arguments

  * `A::Array|CellArray|TArray|TCellArray`: the array to be filled with `x`.
  * `x::Number|Data.Index|Enum|Collection{Number|Data.Index|Enum, celldims}`: the content to fill `A` with. If `A` is an CellArray, then `x` can be either a single value or a collection of values (e.g. an array, tuple,...) of the size `celldims` of `A`.

See also: [`@fill`](@ref)
