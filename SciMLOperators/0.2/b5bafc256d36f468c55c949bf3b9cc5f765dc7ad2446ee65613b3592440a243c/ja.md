```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

ゼロ関数を表す演算子 `n(u) = 0 * u`
