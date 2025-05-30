```julia
struct IdentityOperator <: SciMLOperators.AbstractSciMLOperator{Bool}
```

恒等関数を表すオペレーター `id(v) = v`
