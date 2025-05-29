```
labelmap(obj) -> Dict
```

Computes a mapping from the labels in `obj` to all the individual element-indices in `obj` that correspond to that label

```
julia> labelmap([0, 1, 1, 0, 0])
Dict{Int64,Array{Int64,1}} with 2 entries:
  0 => [1,4,5]
  1 => [2,3]
```
