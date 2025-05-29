```
monic(p::AbstractPolynomialLike)
```

Returns `p / leading_coefficient(p)` where the leading coefficient of the returned polynomials is made sure to be exactly one to avoid rounding error.
