```
CubatureJLp(; error_norm=Cubature.INDIVIDUAL)
```

Multidimensional p-adaptive integration from Cubature.jl. This method is based on repeatedly doubling the degree of the cubature rules, until convergence is achieved. The used cubature rule is a tensor product of Clenshaw–Curtis quadrature rules. `error_norm` specifies the convergence criterion  for vector valued integrands. Defaults to `Cubature.INDIVIDUAL`, other options are `Cubature.PAIRED`, `Cubature.L1`, `Cubature.L2`, or `Cubature.LINF`.
