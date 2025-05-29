```
complex_places(K::NumField) -> Vector{InfPlc}
```

Return all infinite complex places of $K$.

# Examples

```jldoctest
julia> K,  = quadratic_field(-5);

julia> complex_places(K)
1-element Vector{InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}}:
 Infinite place corresponding to (Complex embedding corresponding to 0.00 + 2.24 * i of K)
```
