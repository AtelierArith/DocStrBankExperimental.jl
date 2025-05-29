```
number_field(f::NumFieldEmb) -> NumField
```

Return the corresponding number field of the embedding $f$.

# Examples

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K)[1];

julia> number_field(e)
Imaginary quadratic field defined by x^2 + 3
```
