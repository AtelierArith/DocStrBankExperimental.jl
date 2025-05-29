```
callback_value(cb_data, expr::Union{GenericAffExpr, GenericQuadExpr})
```

Return the primal solution of an affine or quadratic expression inside a callback by getting the value for each variable appearing in the expression.

`cb_data` is the argument to the callback function, and the type is dependent on the solver.
