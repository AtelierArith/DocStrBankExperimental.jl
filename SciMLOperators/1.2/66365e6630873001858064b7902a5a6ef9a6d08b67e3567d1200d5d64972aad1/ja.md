```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

ゼロ関数を表すオペレーター `n(v) = 0 * v`
