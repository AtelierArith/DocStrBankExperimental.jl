```
classical_modular_polynomial([R::MPolyRing,] n::Int) -> Poly
```

Returns the classical modular polynomial of level $n as an element of $\mathbf{Z}[x, y]$. If an optional bivariate polynomial $R$ is specified, the polynomial will be evaluated at the variables of $R$.

Modular polynomials are available up to level `59`.
