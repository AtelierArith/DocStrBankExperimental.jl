```
exp(op::SparseOpType; opts...)
```

Operator exponential used, for example, to calculate displacement operators. Uses [`FastExpm.jl.jl`](https://github.com/fmentink/FastExpm.jl) which will return a sparse or dense operator depending on which is more efficient. All optional arguments are passed to `fastExpm` and can be used to specify tolerances.

If you only need the result of the exponential acting on a vector, consider using much faster implicit methods that do not calculate the entire exponential.
