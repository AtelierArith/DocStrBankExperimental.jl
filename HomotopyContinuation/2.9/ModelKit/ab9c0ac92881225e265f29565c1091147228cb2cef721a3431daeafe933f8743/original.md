```
to_dict(expr::Expression, vars::AbstractVector{Variable})
```

Return the coefficients of `expr` w.r.t. the given variables `vars`. Assumes that `expr` is expanded and representing a polynomial. Throws a `PolynomialError` if a rational expression is encountered.
