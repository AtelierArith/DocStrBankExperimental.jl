```
chunk(x, partition_idxs; [npartitions, dims])
```

Partition the array `x` along the dimension `dims` according to the indexes  in `partition_idxs`.

`partition_idxs` must be sorted and contain only positive integers  between 1 and the number of partitions. 

If the number of partition `npartitions` is not provided,  it is inferred from `partition_idxs`.

If `dims` is not provided, it defaults to the last dimension.

See also [`unbatch`](@ref).

# Examples

```jldoctest
julia> x = reshape([1:10;], 2, 5)
2×5 Matrix{Int64}:
 1  3  5  7   9
 2  4  6  8  10

julia> chunk(x, [1, 2, 2, 3, 3])
3-element Vector{SubArray{Int64, 2, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, UnitRange{Int64}}, true}}:
 [1; 2;;]
 [3 5; 4 6]
 [7 9; 8 10]
```
