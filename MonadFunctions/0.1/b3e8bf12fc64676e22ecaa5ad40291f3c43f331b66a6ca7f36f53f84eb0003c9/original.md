```
flatten(x)
```

Flatten a list x.

# Example

```jldoctest
julia> flatten([1, [2,3], [4, [5], 6]])
6-element Array{Int64,1}:
 1
 2
 3
 4
 5
 6
```
