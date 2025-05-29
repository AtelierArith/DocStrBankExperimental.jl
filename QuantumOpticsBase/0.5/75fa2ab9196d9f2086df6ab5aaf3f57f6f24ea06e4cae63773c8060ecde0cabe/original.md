```
exp(op::DenseSuperOperator)
```

Superoperator exponential which can, for example, be used to calculate time evolutions. Uses LinearAlgebra's `Base.exp`.

If you only need the result of the exponential acting on an operator, consider using much faster implicit methods that do not calculate the entire exponential.
