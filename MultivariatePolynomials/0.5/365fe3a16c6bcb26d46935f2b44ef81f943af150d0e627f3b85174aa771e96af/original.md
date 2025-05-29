```
degree(t::AbstractTermLike)
```

Returns the *total degree* of the monomial of the term `t`, i.e. `sum(exponents(t))`.

```
degree(t::AbstractTermLike, v::AbstractVariable)
```

Returns the exponent of the variable `v` in the monomial of the term `t`.

### Examples

Calling `degree(x^2*y)` should return 3 which is $2 + 1$. Calling `degree(x^2*y, x)` should return 2 and calling `degree(x^2*y, y)` should return 1.
