```
degree(::AbstractPolynomial)
```

Return the degree of the polynomial, i.e. the highest exponent in the polynomial that has a nonzero coefficient.

For standard basis polynomials the degree of the zero polynomial is defined to be $-1$. For Laurent type polynomials, this is `0`, or `lastindex(p)`. The `firstindex` method gives the smallest power of the indeterminate for the polynomial. The default method assumes the basis polynomials, `βₖ`, have degree `k`.
