```
iszero(p::AbstractPolynomial)
```

Is this a $0$ polynomial.

For most types, the $0$ polynomial is one with no coefficients (coefficient vector `T[]`), though some types have the possibility of trailing zeros. The degree of a zero polynomial is conventionally $-1$, though this is not the convention for Laurent polynomials.
