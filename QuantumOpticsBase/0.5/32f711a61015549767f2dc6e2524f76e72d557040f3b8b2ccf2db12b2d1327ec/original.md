```
exp(op::DenseOpType)
```

Operator exponential used, for example, to calculate displacement operators. Uses LinearAlgebra's `Base.exp`.

If you only need the result of the exponential acting on a vector, consider using much faster implicit methods that do not calculate the entire exponential.
