```julia
semipolynomial_form(
    expr,
    vars,
    degree::Real;
    consts
) -> Tuple{Any, Any}

```

Returns a tuple of two objects:

1. A dictionary of coefficients keyed by monomials in `vars` upto the given `degree`,
2. A residual expression which has all terms not represented as a product of monomial and a coefficient

`degree` should be a nonnegative number.

If  `consts` is set to `true`, then the returned dictionary will contain a key `1` and the corresponding value will be the constant term. If `false`, the constant term will be part of the residual.
