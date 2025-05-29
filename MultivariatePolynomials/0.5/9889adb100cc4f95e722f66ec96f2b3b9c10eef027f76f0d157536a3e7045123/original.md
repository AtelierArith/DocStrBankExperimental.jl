```
coefficient(t::AbstractTermLike)
```

Returns the coefficient of the term `t`.

```
coefficient(p::AbstractPolynomialLike, m::AbstractMonomialLike)
```

Returns the coefficient of the monomial `m` in `p`.

### Examples

Calling `coefficient` on $4x^2y$ should return $4$. Calling `coefficient(2x + 4y^2 + 3, y^2)` should return $4$. Calling `coefficient(2x + 4y^2 + 3, x^2)` should return $0$.
