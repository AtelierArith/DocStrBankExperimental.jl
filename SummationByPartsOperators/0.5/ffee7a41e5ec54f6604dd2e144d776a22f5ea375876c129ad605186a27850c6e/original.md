```
evaluate_coefficients!(xplot, uplot, u, D::AbstractDerivativeOperator)
```

Evaluates the nodal coefficients `u` at a grid associated to the derivative operator `D` and stores the result in `xplot, uplot`. Returns `xplot, uplot`, where `xplot` contains the nodes and `uplot` the corresponding values of `u`.
