```
trim(x::AbstractVector; prop=0.0, count=0)
```

Return an iterator of all elements of `x` that omits either `count` or proportion `prop` of the highest and lowest elements.

The number of trimmed elements could be smaller than specified if several elements equal the lower or upper bound.

To compute the trimmed mean of `x` use `mean(trim(x))`; to compute the variance use `trimvar(x)` (see [`trimvar`](@ref)).

# Example

```jldoctest
julia> collect(trim([5,2,4,3,1], prop=0.2))
3-element Vector{Int64}:
 2
 4
 3
```
