```
complex_embeddings(K::NumField; conjugates::Bool = true) -> Vector{NumFieldEmb}
```

Return the complex embeddings of $K$. If `conjugates` is `false`, only one imaginary embedding per conjugated pairs is returned.

# Examples

```jldoctest
julia> K, a = quadratic_field(-3);

julia> complex_embeddings(K)
2-element Vector{AbsSimpleNumFieldEmbedding}:
 Imaginary embedding with 0.00 + 1.73 * i of K
 Imaginary embedding with 0.00 - 1.73 * i of K

julia> complex_embeddings(K, conjugates = false)
1-element Vector{AbsSimpleNumFieldEmbedding}:
 Imaginary embedding with 0.00 + 1.73 * i of K
```
