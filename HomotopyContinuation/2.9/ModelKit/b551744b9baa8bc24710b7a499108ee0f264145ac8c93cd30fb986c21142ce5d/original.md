```
exponents_coefficients(f::Expression, vars::AbstractVector{Variable}; expanded = false)
```

Return a matrix `M` containing the exponents for all occuring terms (one term per column) and a vector `c` containing the corresponding coefficients. Expands the given expression `f` unless `expanded = true`. Throws a `PolynomialError` if a rational expression is encountered.
