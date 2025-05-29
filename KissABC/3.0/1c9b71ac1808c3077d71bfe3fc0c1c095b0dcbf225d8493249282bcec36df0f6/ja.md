```
ApproxPosterior(
    prior::Distribution,
    cost::Function,
    max_cost::Real
)
```

この関数は、`sample` 関数で ABC 密度として使用できる型を返します。この型は、[-ϵ,ϵ] 内で一様に分布した誤差を仮定することによって機能します。ϵ は変数 `max_cost` で指定されます。
