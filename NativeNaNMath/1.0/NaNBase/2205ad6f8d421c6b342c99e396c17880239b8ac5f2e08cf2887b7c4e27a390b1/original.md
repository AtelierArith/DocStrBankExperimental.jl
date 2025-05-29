```
skipnan(itr)
```

Return an iterator over the elements in `itr` skipping NaN values. The returned object can be indexed using indices of `itr` if the latter is indexable. Indices corresponding to NaN values are not valid: they are skipped by [`keys`](@ref) and [`eachindex`](@ref), and a `ErrorException` is thrown when trying to use them. Use [`collect`](@ref) to obtain an `Array` containing the non-`NaN` values in `itr`. Note that even if `itr` is a multidimensional array, the result will always be a `Vector` since it is not possible to remove NaNs while preserving dimensions of the input.

# Examples

```jldoctest
julia> x = skipnan([1, NaN, 2])
skipnan([1.0, NaN, 2.0])
julia> sum(x)
3
julia> x[1]
1
julia> x[2]
ERROR: the value at index (2,) is NaN
[...]
julia> argmax(x)
3
julia> collect(keys(x))
2-element Vector{Int64}:
 1
 3
julia> collect(skipnan([1, NaN, 2]))
2-element Vector{Float64}:
 1.0
 2.0
julia> collect(skipnan([1 NaN; 2 NaN]))
2-element Vector{Float64}:
 1.0
 2.0
```
