```
periodic_derivative_operator(derivative_order, accuracy_order, grid,
                             left_offset=-(accuracy_order+1)÷2, mode=FastMode())
```

Create a `PeriodicDerivativeOperator` approximating the `derivative_order`-th derivative on the uniform `grid` up to order of accuracy `accuracy_order` where the leftmost grid point used is determined by `left_offset`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode())`.
