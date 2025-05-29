```julia
struct IdentityOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

恒等関数 `id(u) = u` を表すオペレーター
