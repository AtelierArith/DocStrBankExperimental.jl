```
function regrid(data, eval_points, basis=PHS(3; poly_deg=2); k=autoselect_k(data, basis))
```

`data` から `eval_points` への再グリッドを行う `RadialBasisOperator` を構築します。
