```
ApproxKernelizedPosterior(
    prior::Distribution,
    cost::Function,
    target_average_cost::Real
)
```

この関数は、`sample`関数でABC密度として使用できる型を返します。この型は、ガウス分布の誤差 𝒩(0,ϵ) を仮定することによって機能し、ϵは変数 `target_average_cost` で指定されます。
