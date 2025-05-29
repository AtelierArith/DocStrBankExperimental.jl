```
conj(f::NumFieldEmb) -> NumFieldEmb
```

Returns the conjugate embedding of `f`.

# Examples

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K);

julia> conj(e[1]) == e[2]
true
```
