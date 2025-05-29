```
properties(x)
```

Iterate through the names and value of the properties of `x`.

```jldoctest
julia> collect(properties(1 + 2im))
2-element Vector{Any}:
 (:re, 1)
 (:im, 2)
```
