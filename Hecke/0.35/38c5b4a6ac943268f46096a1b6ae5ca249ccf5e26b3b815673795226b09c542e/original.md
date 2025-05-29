```
atkin_modular_polynomial([R::MPolyRing,] n::Int) -> Poly
```

Returns the Atkin modular polynomial of prime level $n as an element of $\mathbf{Z}[x, y]$. If an optional bivariate polynomial $R$ is specified, the polynomial will be evaluated at the variables of $R$.

Atkin modular polynomials are available up to level `400`.
