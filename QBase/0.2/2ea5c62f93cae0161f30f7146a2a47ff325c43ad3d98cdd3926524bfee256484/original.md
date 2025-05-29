```
stirling2_partitions( n :: Int64, k :: Int64 ) :: Vector{Vector{Vector{Int64}}}
```

Enumerates the unique partitions of `n` items into `k` unlabelled sets. Each partition is a vector containing a  set of `k` vectors designating each group.

E.g.

```jldoctest
julia> stirling2_partitions( 4, 2 )
7-element Array{Array{Array{Int64,1},1},1}:
 [[1, 2, 3], [4]]
 [[3], [1, 2, 4]]
 [[1, 2], [3, 4]]
 [[1, 3], [2, 4]]
 [[2], [1, 3, 4]]
 [[2, 3], [1, 4]]
 [[1], [2, 3, 4]]
```

This recursive algorithm was inspired by [this blog](https://devblogs.microsoft.com/oldnewthing/20140324-00/?p=1413).
