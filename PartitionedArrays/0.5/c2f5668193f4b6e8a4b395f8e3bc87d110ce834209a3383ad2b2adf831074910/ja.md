```
consistent!(a::PVector) -> Task
```

`a`のローカル値をグローバルに一貫性のあるものにします。つまり、ゴースト値は、関連するグローバルIDを所有する部分の対応する自身の値で更新されます。

# 例

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((2,));

julia> row_partition = uniform_partition(rank,6,true);

julia> map(local_to_global,row_partition)
2-element Vector{PartitionedArrays.BlockPartitionLocalToGlobal{1, Vector{Int32}}}:
 [1, 2, 3, 4]
 [3, 4, 5, 6]

julia> a = pvector(inds->fill(part_id(inds),length(inds)),row_partition)
6-element PVector partitioned into 2 parts of type Vector{Int32}

julia> local_values(a)
2-element Vector{Vector{Int32}}:
 [1, 1, 1, 1]
 [2, 2, 2, 2]

julia> consistent!(a) |> wait

julia> local_values(a)
2-element Vector{Vector{Int32}}:
 [1, 1, 1, 2]
 [1, 2, 2, 2]
```
