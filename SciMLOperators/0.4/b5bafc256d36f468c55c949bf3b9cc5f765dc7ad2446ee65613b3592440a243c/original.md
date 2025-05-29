```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

Operator representing the null function `n(u) = 0 * u`
