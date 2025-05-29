`string_partition_tuple(tuple)`

converts  the partition tuple `tuple` to  a string where the partitions are separated by a dot.

```julia-repl
julia> d=partition_tuples(3,2)
10-element Vector{Vector{Vector{Int64}}}:
 [[1, 1, 1], []]
 [[1, 1], [1]]
 [[1], [1, 1]]
 [[], [1, 1, 1]]
 [[2, 1], []]
 [[1], [2]]
 [[2], [1]]
 [[], [2, 1]]
 [[3], []]
 [[], [3]]

julia> string_partition_tuple.(d)
10-element Vector{String}:
 "111."
 "11.1"
 "1.11"
 ".111"
 "21."
 "1.2"
 "2.1"
 ".21"
 "3."
 ".3"
```
