```
is_imaginary(f::NumFieldEmb) -> Bool
```

Returns `true` if the embedding is imaginary, that is, not real.

# Examples

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K)[1];

julia> is_imaginary(e)
true
```
