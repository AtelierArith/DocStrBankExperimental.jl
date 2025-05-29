```
nterms(p::AbstractPolynomialLike)
```

Returns the number of nonzero terms in `p`, i.e. `length(terms(p))`.

### Examples

Calling `nterms` on $4x^2y + xy + 2x$ should return 3.
