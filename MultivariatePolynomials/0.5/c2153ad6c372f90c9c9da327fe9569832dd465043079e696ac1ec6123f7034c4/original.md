```
exponents(t::AbstractTermLike)
```

Returns the exponent of the variables in the monomial of the term `t`.

### Examples

Calling `exponents(x^2*y)` should return `(2, 1)`.
