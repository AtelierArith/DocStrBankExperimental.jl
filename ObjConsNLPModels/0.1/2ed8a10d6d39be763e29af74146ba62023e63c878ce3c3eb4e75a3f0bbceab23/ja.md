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

`objcons_function`が`[objective, constraints...]`を返す`AbstractNLPModel`を作成します。
