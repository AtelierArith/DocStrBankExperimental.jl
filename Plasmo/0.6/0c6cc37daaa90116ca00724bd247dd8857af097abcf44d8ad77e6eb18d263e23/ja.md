```
JuMP.add_nonlinear_operator(
    graph::OptiGraph,
    dim::Int,
    f::Function,
    args::Vararg{Function,N};
    name::Symbol=Symbol(f),
) where {N}
```

`graph`に非線形演算子を追加します。
