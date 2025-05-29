```
exp(op::SparseSuperOperator; opts...)
```

Superoperator exponential which can, for example, be used to calculate time evolutions. Uses [`FastExpm.jl.jl`](https://github.com/fmentink/FastExpm.jl) which will return a sparse or dense operator depending on which is more efficient. All optional arguments are passed to `fastExpm` and can be used to specify tolerances.

If you only need the result of the exponential acting on an operator, consider using much faster implicit methods that do not calculate the entire exponential.
