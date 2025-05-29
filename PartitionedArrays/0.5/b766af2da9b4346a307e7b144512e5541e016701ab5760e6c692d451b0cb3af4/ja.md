```
tuple_of_arrays(a)
```

配列のタプル `a` を配列のタプルに変換します。

# 例

```jldoctest
julia> using PartitionedArrays

julia> a = [(1,2),(3,4),(5,6)]
3-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (3, 4)
 (5, 6)

julia> b,c = tuple_of_arrays(a)
([1, 3, 5], [2, 4, 6])
```
