```
p = get_polynomial(graph::Compgraph)
```

Return the polynomial underlying the computational `graph`. The `graph` is assumed to involve only linear combinations and multiplications.

`p` is polynomial of type `Polynomial` from the package [`Polynomials.jl`](https://juliamath.github.io/Polynomials.jl/stable/).

See also [`get_polynomial_coefficients`](@ref).
