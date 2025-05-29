```
is_real(f::NumFieldEmb) -> Bool
```

Return `true` if the embedding is real.

# Examples

```jldoctest
julia> K, a = quadratic_field(3); e = complex_embeddings(K)[1];

julia> is_real(e)
true
```
