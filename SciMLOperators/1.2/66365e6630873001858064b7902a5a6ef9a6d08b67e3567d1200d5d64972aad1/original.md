```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

Operator representing the null function `n(v) = 0 * v`
