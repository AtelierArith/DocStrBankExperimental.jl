```
assemble!([op,] a::PVector) -> Task
```

Transfer the ghost values to their owner part and insert them according with the insertion operation `op` (`+` by default). It returns a task that produces `a` with updated values. After the transfer, the source ghost values are set to zero.

# Examples

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
