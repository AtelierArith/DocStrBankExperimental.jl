```
lobatto_quadrature(q, mode::Mode=Abscissa)
```

Return the Gauss-Lobatto quadrature rule with `q` points (integrates polynomials of degree $2q-3$ exactly).

If `mode` is `AbscissaAndWeights`, then both the weights and abscissa are returned as a tuple `(x,w)`.

Otherwise, (if `mode` is `Abscissa`), then only the abscissa `x` are returned.
