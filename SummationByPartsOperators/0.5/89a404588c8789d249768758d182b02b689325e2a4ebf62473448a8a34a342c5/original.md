```
var_coef_derivative_operator(source_of_coefficients, derivative_order, accuracy_order,
                             xmin, xmax, N, left_weights, right_weights, bfunc,
                             mode=FastMode())
```

Create a `VarCoefDerivativeOperator` approximating a `derivative_order`-th derivative with variable coefficients `bfunc` on a grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order` with coefficients given by `source_of_coefficients`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
