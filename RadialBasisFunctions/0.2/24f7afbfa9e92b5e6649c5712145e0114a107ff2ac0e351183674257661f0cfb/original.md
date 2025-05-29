```
function regrid(data, eval_points, basis=PHS(3; poly_deg=2); k=autoselect_k(data, basis))
```

Builds a `RadialBasisOperator` where the operator is an regrid from one set of points to another, `data` -> `eval_points`.
