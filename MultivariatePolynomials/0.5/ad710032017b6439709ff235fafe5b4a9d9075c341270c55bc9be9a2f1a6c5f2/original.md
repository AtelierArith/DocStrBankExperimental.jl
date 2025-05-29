```
leading_coefficient(p::AbstractPolynomialLike)
```

Returns the coefficient of the leading term of `p`, i.e. `coefficient(leading_term(p))`.

### Examples

Calling `leading_coefficient` on $4x^2y + xy + 2x$ should return $4$ and calling it on $0$ should return $0$.
