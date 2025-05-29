```
embeddings(p::InfPlc) -> Vector{NumFieldEmb}
```

Given a complex place, return all complex embeddings defining this place.

See also [`embedding`](@ref).

# Examples

```jldoctest
julia> K,  = quadratic_field(-5);

julia> embeddings(complex_places(K)[1])
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Complex embedding corresponding to 0.00 + 2.24 * i of K
 Complex embedding corresponding to 0.00 - 2.24 * i of K
```
