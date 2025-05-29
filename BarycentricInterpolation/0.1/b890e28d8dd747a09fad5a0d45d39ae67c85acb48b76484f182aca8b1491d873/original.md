```
differentiation_matrix(poly::AbstractPolynomial)
```

Return the differentiation matrix at the nodes of the polynomial specified.

```
P = Chebyshev2{5}()
D = differentiation_matrix(P)
```

Now dy/dx ≈ `D*y` at the nodes of the polynomial.
