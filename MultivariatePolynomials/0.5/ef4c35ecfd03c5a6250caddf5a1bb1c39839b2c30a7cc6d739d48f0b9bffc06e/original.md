```
monomial_vector(X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

Returns the vector of monomials `X` in increasing order and without any duplicates.

### Examples

Calling `monomial_vector` on $[xy, x, xy, x^2y, x]$ should return $[x^2y, xy, x]$.
