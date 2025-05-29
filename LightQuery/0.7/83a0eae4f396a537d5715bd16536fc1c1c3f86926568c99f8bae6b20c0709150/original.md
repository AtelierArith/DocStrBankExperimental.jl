```
Backwards(something)
```

Reverse sorting order.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> collect(@inferred order([1, -2], Backwards))
2-element Array{Int64,1}:
  1
 -2
```
