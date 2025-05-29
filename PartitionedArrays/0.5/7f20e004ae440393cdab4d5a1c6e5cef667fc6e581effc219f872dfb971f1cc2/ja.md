```
find_owner(index_partition,global_ids)
```

`global_ids`内のグローバルIDの所有者を見つけます。入力の`global_ids`は、`index_partition`と同じ部分に分配されたベクトルのベクトルです。各部分は、並列バックエンドを使用する場合、所有者を並行して探します。

# 例

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((4,));

julia> index_partition = uniform_partition(rank,10)
4-element Vector{PartitionedArrays.LocalIndicesWithConstantBlockSize{1}}:
 [1, 2]
 [3, 4]
 [5, 6, 7]
 [8, 9, 10]

julia> gids = [[3],[4,5],[7,2],[9,10,1]]
4-element Vector{Vector{Int64}}:
 [3]
 [4, 5]
 [7, 2]
 [9, 10, 1]

julia> find_owner(index_partition,gids)
4-element Vector{Vector{Int32}}:
 [2]
 [2, 3]
 [3, 1]
 [4, 4, 1]
```
