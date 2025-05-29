```
evaluate_coefficients!(xplot, uplot, u, basis::NodalBasis{Line})
```

Evaluate the coefficients `u` of the nodal basis `basis` at `npoints` equally spaced nodes and store the result in `xplot, uplot`. Returns `xplot, uplot`, where `xplot` contains the equally spaced nodes and `uplot` the corresponding values of `u`.
