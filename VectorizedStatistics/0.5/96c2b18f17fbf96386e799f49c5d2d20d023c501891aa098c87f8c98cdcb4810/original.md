```julia
vsort!([I], A; dims, multithreaded=false)
```

Sort the array `A`, optionally along dimensions specified by `dims`.

If the optional argument `I` is supplied, it will be sorted following the same permuation as `A`. For example, if `I = collect(1:length(A))`, then after calling `vsort!(I, A)`, `A` will be sorted and `I` will be equal to `sortperm(A)`

If sorting over multiple `dims`, these dimensions must be contiguous (i.e. `dims=(2,3)` but not `dims=(1,3)`). Note also that specifying `dims` other than `:` creates `view`s, with some nonezero performance cost.

## Examples

```julia
julia> using VectorizedStatistics

julia> A = [1, 3, 2, 4];

julia> vsort!(A)
4-element Vector{Int64}:
 1
 2
 3
 4
```
