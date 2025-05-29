```
scan(op,a;init,type)
```

Return the scan of the values in `a` for the operation `op`. Use `type=:inclusive` or `type=:exclusive` to use an inclusive or exclusive scan. `init` will be added to all items in the result. Additionally, for exclusive scans, the first item in the result will be set to `init`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> a = [2,4,1,3]
4-element Vector{Int64}:
 2
 4
 1
 3

julia> scan(+,a,type=:inclusive,init=0)
4-element Vector{Int64}:
  2
  6
  7
 10

julia> scan(+,a,type=:exclusive,init=1)
4-element Vector{Int64}:
 1
 3
 7
 8
```
