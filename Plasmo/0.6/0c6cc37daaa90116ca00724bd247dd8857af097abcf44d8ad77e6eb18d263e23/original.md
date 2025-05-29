```
JuMP.add_nonlinear_operator(
    graph::OptiGraph,
    dim::Int,
    f::Function,
    args::Vararg{Function,N};
    name::Symbol=Symbol(f),
) where {N}
```

Add a nonlinear operator to a `graph`.
