```julia
DeriDistFunction(E ; T::Float64, mu::Float64=0.0, stat::Int64=-1)
```

エネルギーに関する [`dist`](@ref) の導関数。 `stat`=1 → ボース-アインシュタイン分布、`stat`=-1 → フェルミ分布。
