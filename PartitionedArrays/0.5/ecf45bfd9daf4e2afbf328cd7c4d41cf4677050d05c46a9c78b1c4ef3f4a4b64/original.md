```
reduction(op, a; destination=MAIN [,init])
```

Reduce the values in array `a` according with operation `op` and the initial value `init` and store the result in a new array of the same size as `a` at index `destination`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> a = [1,3,2,4]
4-element Vector{Int64}:
 1
 3
 2
 4

julia> reduction(+,a;init=0,destination=2)
4-element Vector{Int64}:
  0
 10
  0
  0
```
