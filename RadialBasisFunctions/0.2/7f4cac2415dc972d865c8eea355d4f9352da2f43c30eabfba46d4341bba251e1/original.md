```
function partial(data, eval_points, order, dim, basis; k=autoselect_k(data, basis))
```

Builds a `RadialBasisOperator` where the operator is the partial derivative, `Partial`. The resulting operator will only evaluate at `eval_points`.
