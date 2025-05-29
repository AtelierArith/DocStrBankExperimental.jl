```
sort_monomial_vector(X::AbstractVector{MT}) where {MT<:AbstractMonomialLike}
```

Returns `σ`, the orders in which one must take the monomials in `X` to make them sorted and without any duplicate and the sorted vector of monomials, i.e. it returns `(σ, X[σ])`.

### Examples

Calling `sort_monomial_vector` on $[xy, x, xy, x^2y, x]$ should return $([4, 1, 2], [x^2y, xy, x])$.
