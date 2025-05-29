```
fieldvalues(x)
```

Iterate through the values of the fields of `x`.

```jldoctest
julia> collect(fieldvalues(1 + 2im))
2-element Vector{Any}:
 1
 2
```
