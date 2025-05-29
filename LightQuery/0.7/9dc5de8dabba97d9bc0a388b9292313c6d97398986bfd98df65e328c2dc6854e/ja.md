```
Length(iterator, new_length)
```

長さに基づく最適化を許可します。

```jldoctest
julia> using LightQuery


julia> collect(Length(Iterators.filter(iseven, 1:4), 2))
2-element Array{Int64,1}:
 2
 4
```
