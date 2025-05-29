```
function gradient(data, eval_points, basis; k=autoselect_k(data, basis))
```

Builds a `RadialBasisOperator` where the operator is the gradient, `Gradient`. The resulting operator will only evaluate at `eval_points`.
