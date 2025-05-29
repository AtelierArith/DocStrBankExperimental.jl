```julia
polynomial_coeffs(expr, vars)

```

Find coefficients of a polynomial in `vars`.

Returns a tuple of two elements:

1. A dictionary of coefficients keyed by monomials in `vars`
2. A residual expression which is the constant term

(Same as `semipolynomial_form(expr, vars, Inf)`)
