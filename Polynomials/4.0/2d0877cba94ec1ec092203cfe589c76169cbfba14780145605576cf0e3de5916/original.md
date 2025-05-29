```
coeffs(::AbstractPolynomial)
coeffs(::AbstractDenseUnivariatePolynomial)
coeffs(::AbstractLaurentUnivariatePolynomial)
```

For a dense, univariate polynomial return the coefficients $(a_0, a_1, \dots, a_n)$ as an interable. This may be a vector or tuple, and may alias the polynomials coefficients.

For a Laurent type polynomial (e.g. `LaurentPolynomial`, `SparsePolynomial`) return the coefficients $(a_i, a_{i+1}, \dots, a_j)$ where $i$ is found from `firstindex(p)` and $j$ from `lastindex(p)`.

For `LaurentPolynomial` and `SparsePolynomial`, the `pairs` iterator is more generically useful, as it iterates over $(i, p_i)$ possibly skipping the terms where $p_i = 0$.

Defaults to `p.coeffs`.
