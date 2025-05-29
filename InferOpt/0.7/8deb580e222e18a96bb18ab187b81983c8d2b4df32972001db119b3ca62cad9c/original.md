```julia
objective_value(
    f::InferOpt.LinearMaximizer,
    θ,
    y;
    kwargs...
) -> Any

```

Computes the objective value of given LinearMaximizer `f`, knowing weights `θ` and solution `y`. i.e. θᵀg(y) + h(y)
