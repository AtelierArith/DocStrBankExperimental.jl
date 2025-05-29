```
periodic_central_derivative_operator(derivative_order, accuracy_order,
                                     xmin, xmax, N, mode=FastMode())
```

Create a [`PeriodicDerivativeOperator`](@ref) approximating the `derivative_order`-th derivative on a uniform grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
