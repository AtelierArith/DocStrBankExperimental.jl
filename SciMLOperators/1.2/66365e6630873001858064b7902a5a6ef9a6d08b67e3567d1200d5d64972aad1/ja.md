```julia
struct NullOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

ゼロ関数 `n(v) = 0 * v` を表すオペレーター
