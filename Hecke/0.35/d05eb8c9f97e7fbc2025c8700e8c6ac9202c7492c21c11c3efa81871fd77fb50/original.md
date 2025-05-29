```
signs(a::NumFieldElem, [embs::Vector{NumFieldEmb} = real_embeddings(K)])
                                                   -> Dict{NumFieldEmb, Int}
```

Return the signs of `a` at the real embeddings in `embs` as a dictionary, which are by default all real embeddings of the number field.

# Examples

```jldoctest; filter = r"Complex.*"
julia> K, a = quadratic_field(3);

julia> signs(a)
Dict{AbsSimpleNumFieldEmbedding, Int64} with 2 entries:
  Complex embedding corresponding to -1.73 of real quadratic field define… => -1
  Complex embedding corresponding to 1.73 of real quadratic field defined… => 1
```
