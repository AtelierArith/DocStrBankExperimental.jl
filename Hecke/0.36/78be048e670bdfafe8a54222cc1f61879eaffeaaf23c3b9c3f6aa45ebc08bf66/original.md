```
real_embeddings(K::NumField) -> Vector{NumFieldEmb}
```

Return the real embeddings of $K$.

# Examples

```jldoctest
julia> K, a = quadratic_field(3);

julia> real_embeddings(K)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Real embedding with -1.73 of K
 Real embedding with 1.73 of K
```
