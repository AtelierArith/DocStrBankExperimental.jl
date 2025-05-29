```julia
unionize(x::AbstractVector)
```

Turn an array with possibly abstract element type into one with  `eltype` equal to a Union of all types of elements in the array.

Always returns a copy, even if `x` is already unionized.

### Examples

```julia
julia> a = Any[false, 0, 1.0]
3-element Vector{Any}:
 false
     0
     1.0

julia> unionize(a)
3-element Vector{Union{Bool, Float64, Int64}}:
 false
     0
     1.0
```
