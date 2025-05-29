```
setindex!(x::GapObj, v::Any, i::Int64)
setindex!(x::GapObj, v::Any, i::Int64, j::Int64)
setindex!(x::GapObj, v::Any, l::Union{Vector{T},AbstractRange{T}}) where {T<:Integer}
```

Set the entry at position `i` or `(i,j)` in `x` to `v`, or set the entries at the positions in `x` that are described by `l` to the entries in `v`, provided that `x` is a GAP object supporting this, such as a GAP list or matrix object.

# Examples

```jldoctest
julia> l = GapObj([ 1, 2, 3, 5, 8, 13 ])
GAP: [ 1, 2, 3, 5, 8, 13 ]

julia> l[1] = 0
0

julia> l[8] = -1
-1

julia> l[2:4] = [ 7, 7, 7 ]
3-element Vector{Int64}:
 7
 7
 7

julia> l
GAP: [ 0, 7, 7, 7, 8, 13,, -1 ]

julia> m = GapObj([ 1 2 ; 3 4 ])
GAP: [ [ 1, 2 ], [ 3, 4 ] ]

julia> m[1,2] = 0
0

julia> m
GAP: [ [ 1, 0 ], [ 3, 4 ] ]
```
