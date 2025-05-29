```
basevec(::Type{Vec{dim, T}})
basevec(::Type{Vec{dim, T}}, i)
basevec(::Vec{dim, T})
basevec(::Vec{dim, T}, i)
```

Return a tuple with the base vectors corresponding to the dimension `dim` and type `T`. An optional integer `i` can be used to extract the i:th base vector. The alias `eᵢ` can also be used, written `e\_i<TAB>`.

# Examples

```jldoctest
julia> eᵢ(Vec{2, Float64})
([1.0, 0.0], [0.0, 1.0])

julia> eᵢ(Vec{2, Float64}, 2)
2-element Vec{2, Float64}:
 0.0
 1.0
```
