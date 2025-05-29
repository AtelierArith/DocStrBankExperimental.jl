```
propertyvalues(x)
```

Iterate through the values of the properties of `x`.

```jldoctest
julia> collect(propertyvalues(1 + 2im))
2-element Vector{Any}:
 1
 2
```
