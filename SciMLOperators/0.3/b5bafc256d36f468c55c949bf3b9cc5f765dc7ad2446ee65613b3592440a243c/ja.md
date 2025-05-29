```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

ゼロ関数を表すオペレーター `n(u) = 0 * u`
