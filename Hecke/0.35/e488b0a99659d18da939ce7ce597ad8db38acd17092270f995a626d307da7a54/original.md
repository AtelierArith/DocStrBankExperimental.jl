```
real_embeddings(K::NumField) -> Vector{NumFieldEmb}
```

Return the real embeddings of $K$.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> real_embeddings(K)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Complex embedding corresponding to -1.73 of K
 Complex embedding corresponding to 1.73 of K
```
