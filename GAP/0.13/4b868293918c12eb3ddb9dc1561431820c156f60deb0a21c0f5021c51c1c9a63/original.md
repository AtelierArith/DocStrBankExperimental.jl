```
getindex(x::GapObj, i::Int64)
getindex(x::GapObj, i::Int64, j::Int64)
getindex(x::GapObj, l::Union{Vector{T},AbstractRange{T}}) where {T<:Integer}
```

Return the entry at position `i` or at position `(i,j)` in `x`, or the list of entries in `x` at the positions described by `l`, provided that `x` is a GAP object supporting this, such as a GAP list or matrix object.

# Examples

```jldoctest
julia> l = GapObj([ 1, 2, 3, 5, 8, 13 ])
GAP: [ 1, 2, 3, 5, 8, 13 ]

julia> l[4]
5

julia> l[end]
13

julia> l[2:4]
GAP: [ 2, 3, 5 ]

julia> l[[1,4,4]]
GAP: [ 1, 5, 5 ]

julia> m = GapObj([ 1 2 ; 3 4 ])
GAP: [ [ 1, 2 ], [ 3, 4 ] ]

julia> m[1,1]
1

julia> m[1,2]
2

julia> m[2,1]
3
```
