```
function partial(data, order, dim, basis; k=autoselect_k(data, basis))
```

Builds a `RadialBasisOperator` where the operator is the partial derivative, `Partial`, of `order` with respect to `dim`.
