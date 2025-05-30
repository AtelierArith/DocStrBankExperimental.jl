```julia
struct IdentityOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

恒等関数 `id(v) = v` を表すオペレーター
