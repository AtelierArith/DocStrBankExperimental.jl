```
c = get_polynomial_coefficients(graph::Compgraph)
```

Return the coefficients of the polynomial underlying the computational `graph`. The `graph` is assumed to involve only linear combinations and multiplications.

The coefficients `c` is a vector containing the coefficients as expressed in the monomial basis and sorted from the leading coefficient to the constant term.

See also [`get_polynomial`](@ref).
