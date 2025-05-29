```
static_operator(op::AbstractOperator)
```

Returns a static (not time dependent) representation of `op` the current time. This strips the time-dependence and can be used to obtain a non-lazy matrix representation of the operator.

For example: `sparse(static_operator(op(t))` return a sparse-matrix representation of `op` at time `t`.
