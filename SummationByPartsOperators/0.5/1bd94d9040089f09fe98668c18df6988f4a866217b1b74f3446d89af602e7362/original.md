```
derivative_operator(source_of_coefficients,
                    derivative_order, accuracy_order,
                    xmin, xmax, N, mode=FastMode())
derivative_operator(source_of_coefficients;
                    derivative_order, accuracy_order,
                    xmin, xmax, N, mode=FastMode())
```

Create a [`DerivativeOperator`](@ref) approximating the `derivative_order`-th derivative on a grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order`. with coefficients given by `source_of_coefficients`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
