```julia
objcons_nlpmodel(
    objcons_function;
    x0,
    lvar,
    uvar,
    min_cache_size,
    max_cache_size
)

```

Create an `AbstractNLPModel` where `objcons_function` returns `[objective, constraints...]`.
