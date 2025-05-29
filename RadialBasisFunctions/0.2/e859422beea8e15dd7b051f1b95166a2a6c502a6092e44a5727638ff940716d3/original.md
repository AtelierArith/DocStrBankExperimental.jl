```
function ∂virtual(data, eval_points, dim, Δ, basis; k=autoselect_k(data, basis))
```

Builds a virtual `RadialBasisOperator` whichi will be evaluated at `eval_points` where the operator is the partial derivative with respect to `dim`. Virtual operators interpolate the data to structured points at a distance `Δ` for which standard finite difference formulas can be applied.
