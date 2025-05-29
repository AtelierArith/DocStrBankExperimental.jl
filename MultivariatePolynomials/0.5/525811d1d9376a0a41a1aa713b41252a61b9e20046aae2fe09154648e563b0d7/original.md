```
terms(p::AbstractPolynomialLike)
```

Returns an iterator over the nonzero terms of the polynomial `p` sorted in the decreasing monomial order.

### Examples

Calling `terms` on $4x^2y + xy + 2x$ should return an iterator of $[4x^2y, xy, 2x]$.
