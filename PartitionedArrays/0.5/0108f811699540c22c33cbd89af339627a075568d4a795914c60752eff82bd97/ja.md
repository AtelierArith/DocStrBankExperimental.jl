```
assemble!([op,] a::PVector) -> Task
```

ゴースト値をその所有者部分に転送し、挿入操作 `op`（デフォルトは `+`）に従って挿入します。更新された値を持つ `a` を生成するタスクを返します。転送後、ソースのゴースト値はゼロに設定されます。

# 例

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((2,));

julia> row_partition = uniform_partition(rank,6,true);

julia> map(local_to_global,row_partition)
2-element Vector{PartitionedArrays.BlockPartitionLocalToGlobal{1, Vector{Int32}}}:
 [1, 2, 3, 4]
 [3, 4, 5, 6]

julia> a = pones(row_partition)
6-element PVector partitioned into 2 parts of type Vector{Float64}

julia> local_values(a)
2-element Vector{Vector{Float64}}:
 [1.0, 1.0, 1.0, 1.0]
 [1.0, 1.0, 1.0, 1.0]

julia> assemble!(a) |> wait

julia> local_values(a)
2-element Vector{Vector{Float64}}:
 [1.0, 1.0, 2.0, 0.0]
 [0.0, 2.0, 1.0, 1.0]
```
