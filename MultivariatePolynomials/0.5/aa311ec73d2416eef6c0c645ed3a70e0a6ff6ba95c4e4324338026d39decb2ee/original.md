```
leading_term(p::AbstractPolynomialLike)
```

Returns the leading term, i.e. `last(terms(p))`.

### Examples

Calling `leading_term` on $4x^2y + xy + 2x$ should return $4x^2y$.
