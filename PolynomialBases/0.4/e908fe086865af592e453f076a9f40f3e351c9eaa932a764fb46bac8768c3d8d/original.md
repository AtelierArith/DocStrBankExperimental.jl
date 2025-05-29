```
evaluate_coefficients(u, basis::NodalBasis{Line}, npoints=2*length(basis.nodes))
```

Evaluate the coefficients `u` of the nodal basis `basis` at `npoints` equally spaced nodes. Returns `xplot, uplot`, where `xplot` contains the equally spaced nodes and `uplot` the corresponding values of `u`.
