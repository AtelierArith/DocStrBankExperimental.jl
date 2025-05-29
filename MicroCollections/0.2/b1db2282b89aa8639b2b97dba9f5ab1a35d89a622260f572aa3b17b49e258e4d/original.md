```
OneHotArray(index => value, shape) -> array::AbstractArray
```

Create an `array` such that `isequal(array[index], value)`.  The values at indices other than `index` are undefined.

Currently, this array type is likely only useful as the second argument to `BangBang.Extras.broadcast_inplace!!` and as the input argument to FLoops.jl's  `@reduce`

# Examples

```jldoctest
julia> using MicroCollections, BangBang.Extras

julia> broadcast_inplace!!(+, ones(Int64, 4), OneHotVector(2 => 3, 4))
4-element Vector{Int64}:
 1
 4
 1
 1

julia> using InitialValues

julia> broadcast_inplace!!(+, InitialValue(+), OneHotVector(2 => 3, 4))
4-element Vector{Int64}:
 0
 3
 0
 0
```
