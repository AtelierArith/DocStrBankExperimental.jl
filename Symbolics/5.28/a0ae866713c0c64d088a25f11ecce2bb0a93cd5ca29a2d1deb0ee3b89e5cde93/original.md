```julia
semipolynomial_form(
    exprs::AbstractArray,
    vars,
    degree::Real;
    consts
) -> Tuple{Any, Any}

```

For every expression in `exprs` computes the semi-polynomial form and returns a tuple of two objects – a vector of coefficient dictionaries, and a vector of residual terms.

If  `consts` is set to `true`, then the returned dictionary will contain a key `1` and the corresponding value will be the constant term. If `false`, the constant term will be part of the residual.
