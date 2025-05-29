```
	eval_febe!(result, FEBE::FEBasisEvaluator, j::Int, i::Int, offset::Int = 0, factor = 1)
```

Evaluate the j-th basis function of the FEBasisEvaluator at the i-th quadrature point and writes the (possibly vector-valued) evaluation into result (beginning at offset and with the specified factor).
