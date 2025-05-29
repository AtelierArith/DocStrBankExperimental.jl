```
extend(p::InfPlc, L::NumField) -> Vector{InfPlc}
```

Given an infinite place `p` of a number field `K` and an extension `L` of `K`, return all infinite places of `L` lying above `p`.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> L, b = number_field(polynomial(K, [-2, 0, 0, 1]), "b");

julia> p = infinite_places(K)[1];

julia> extend(p, L)
2-element Vector{InfPlc{Hecke.RelSimpleNumField{AbsSimpleNumFieldElem}, RelSimpleNumFieldEmbedding{AbsSimpleNumFieldEmbedding, Hecke.RelSimpleNumField{AbsSimpleNumFieldElem}}}}:
 Infinite place corresponding to (Complex embedding corresponding to root 1.26 of relative number field)
 Infinite place corresponding to (Complex embedding corresponding to root -0.63 + 1.09 * i of relative number field)
```
