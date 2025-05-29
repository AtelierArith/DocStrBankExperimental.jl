`partitions(set::AbstractVector[,k])`, `npartitions(set::AbstractVector[,k])`

集合 `set` のすべての順序なしの分割の集合（`k` が指定されている場合は `k` 個の集合）を返します。`npartitions` は順序なしの分割の数を返します。

集合 `set` の*順序なしの分割*は、互いに素な集合の集合であり、その和集合が `set` に等しく、ベクトルのベクトルとして表されます。

```julia-repl
julia> npartitions(1:3)
5

julia> partitions(1:3)
5-element Vector{Vector{Vector{Int64}}}:
 [[1, 2, 3]]
 [[1, 2], [3]]
 [[1, 3], [2]]
 [[1], [2, 3]]
 [[1], [2], [3]]

julia> npartitions(1:4,2)
7

julia> partitions(1:4,2)
7-element Vector{Vector{Vector{Int64}}}:
 [[1, 2, 3], [4]]
 [[1, 2, 4], [3]]
 [[1, 2], [3, 4]]
 [[1, 3, 4], [2]]
 [[1, 3], [2, 4]]
 [[1, 4], [2, 3]]
 [[1], [2, 3, 4]]
```

`unique(sort.(partitions(mset[,k])))` は、重複集合 `mset` に対して機能するバージョンであることに注意してください。
