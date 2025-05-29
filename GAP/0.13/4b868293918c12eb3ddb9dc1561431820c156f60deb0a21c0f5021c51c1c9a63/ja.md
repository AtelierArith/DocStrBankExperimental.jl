```
getindex(x::GapObj, i::Int64)
getindex(x::GapObj, i::Int64, j::Int64)
getindex(x::GapObj, l::Union{Vector{T},AbstractRange{T}}) where {T<:Integer}
```

`x`の位置`i`または位置`(i,j)`のエントリを返すか、`l`で説明される位置にある`x`のエントリのリストを返します。`x`は、GAPリストや行列オブジェクトなど、これをサポートするGAPオブジェクトである必要があります。

# 例

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
