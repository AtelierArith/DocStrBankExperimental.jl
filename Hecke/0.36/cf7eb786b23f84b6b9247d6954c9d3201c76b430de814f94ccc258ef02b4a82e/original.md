```
real_places(K::NumField) -> Vector{InfPlc}
```

Return all infinite real places of the number field.

# Examples

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_places(K)
2-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Infinite place of real embedding with -2.24 of K
 Infinite place of real embedding with 2.24 of K
```
