```
find_owner(index_partition,global_ids)
```

Find the owners of the global ids in `global_ids`. The input `global_ids` is a vector of vectors distributed over the same parts as `index_partition`. Each part will look for the owners in parallel, when using a parallel back-end.

# Example

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
