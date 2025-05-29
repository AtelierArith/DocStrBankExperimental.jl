```
principal_subfields(L::SimpleNumField) -> Vector{Tuple{NumField, Map}}
```

Return the principal subfields of $L$ as pairs consisting of a subfield $k$ and an embedding $k \to L$.

# Examples

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^8 - x^4 + 1);

julia> length(principal_subfields(K))
8
```
