```
dissipation_operator(source_of_coefficients, order, xmin, xmax, N,
                     left_weights, right_weights, mode=FastMode())
```

Create a negative semidefinite `DissipationOperator` using undivided differences approximating a weighted `order`-th derivative on a grid between `xmin` and `xmax` with `N` grid points up to order of accuracy 2 with coefficients given by `source_of_coefficients`. The norm matrix is given by `left_weights` and `right_weights`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
