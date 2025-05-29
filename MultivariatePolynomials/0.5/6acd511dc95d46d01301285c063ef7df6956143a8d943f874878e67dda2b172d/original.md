```
leading_monomial(p::AbstractPolynomialLike)
```

Returns the monomial of the leading term of `p`, i.e. `monomial(leading_term(p))` or `last(monomials(p))`.

### Examples

Calling `leading_monomial` on $4x^2y + xy + 2x$ should return $x^2y$.
