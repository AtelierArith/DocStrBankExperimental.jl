```
merge_monomial_vectors{MT<:AbstractMonomialLike, MVT<:AbstractVector{MT}}(X::AbstractVector{MVT}}
```

Returns the vector of monomials in the entries of `X` in increasing order and without any duplicates, i.e. `monomial_vector(vcat(X...))`

### Examples

Calling `merge_monomial_vectors` on $[[xy, x, xy], [x^2y, x]]$ should return $[x^2y, xy, x]$.
