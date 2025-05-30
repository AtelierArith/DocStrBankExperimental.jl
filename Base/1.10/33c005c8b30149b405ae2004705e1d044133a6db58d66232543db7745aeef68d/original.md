```
getindex(A, inds...)
```

Return a subset of array `A` as specified by `inds`, where each `ind` may be, for example, an `Int`, an [`AbstractRange`](@ref), or a [`Vector`](@ref). See the manual section on [array indexing](@ref man-array-indexing) for details.

# Examples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4
```
