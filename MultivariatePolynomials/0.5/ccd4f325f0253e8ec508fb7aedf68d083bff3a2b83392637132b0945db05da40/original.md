```
monomial_vector(a, X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

Returns `b, Y` where `Y` is the vector of monomials of `X` in increasing order and without any duplicates and `b` is the vector of corresponding coefficients in `a`, where coefficients of duplicate entries are summed together.

### Examples

Calling `monomial_vector` on $[2, 1, 4, 3, -1], [xy, x, xy, x^2y, x]$ should return $[3, 6, 0], [x^2y, xy, x]$.
