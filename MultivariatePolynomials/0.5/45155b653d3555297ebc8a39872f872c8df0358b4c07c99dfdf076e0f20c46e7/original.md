```
coefficient(p::AbstractPolynomialLike, m::AbstractMonomialLike, vars)::AbstractPolynomialLike
```

Returns the coefficient of the monomial `m` of the polynomial `p` considered as a polynomial in variables `vars`.

### Example

Calling `coefficient((a+b)x^2+2x+y*x^2, x^2, [x,y])` should return `a+b`. Calling `coefficient((a+b)x^2+2x+y*x^2, x^2, [x])` should return `a+b+y`.
