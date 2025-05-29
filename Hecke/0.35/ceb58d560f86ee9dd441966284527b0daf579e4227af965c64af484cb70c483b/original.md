```
infinite_places(K::NumField) -> Vector{InfPlc}
```

Return all infinite places of the number field.

# Examples

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_places(K)
2-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Infinite place corresponding to (Complex embedding corresponding to -2.24 of K)
 Infinite place corresponding to (Complex embedding corresponding to 2.24 of K)
```
