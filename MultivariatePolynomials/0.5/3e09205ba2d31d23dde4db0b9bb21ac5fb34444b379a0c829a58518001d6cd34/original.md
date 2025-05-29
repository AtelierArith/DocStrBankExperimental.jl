```
coefficients(p::AbstractPolynomialLike)
```

Returns an iterator over the coefficients of `p` of the nonzero terms of the polynomial sorted in the decreasing monomial order.

```
coefficients(p::AbstractPolynomialLike, X::AbstractVector)
```

Returns an iterator over the coefficients of the monomials of `X` in `p` where `X` is a monomial vector not necessarily sorted but with no duplicate entry.

### Examples

Calling `coefficients` on $4x^2y + xy + 2x$ should return an iterator of $[4, 1, 2]$. Calling `coefficients(4x^2*y + x*y + 2x + 3, [x, 1, x*y, y])` should return an iterator of $[2, 3, 1, 0]$.
