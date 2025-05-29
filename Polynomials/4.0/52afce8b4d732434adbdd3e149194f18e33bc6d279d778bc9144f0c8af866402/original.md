```
AbstractUnivariatePolynomial{B,T,X} <: AbstractPolynomial{T,X}
AbstractDenseUnivariatePolynomial{B,T,X} <: AbstractUnivariatePolynomial{B,T,X}
AbstractLaurentUnivariatePolynomial{B,T,X} <: AbstractUnivariatePolynomial{B,T,X}
```

Abstract container types for polynomials with an explicit basis, `B`. `AbstractDenseUnivariatePolynomial` is for `0`-based polynomials; `AbstractLaurentUnivariatePolynomial` is for polynomials with possibly negative powers of the indeterminate.
