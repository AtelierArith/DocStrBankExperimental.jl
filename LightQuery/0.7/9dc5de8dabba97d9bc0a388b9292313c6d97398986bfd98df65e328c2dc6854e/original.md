```
Length(iterator, new_length)
```

Allow optimizations based on length.

```jldoctest
julia> using LightQuery


julia> collect(Length(Iterators.filter(iseven, 1:4), 2))
2-element Array{Int64,1}:
 2
 4
```
