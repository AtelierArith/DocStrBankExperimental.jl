```
convert_eltype(T) -> f
```

yields a callable object `f` such that `f(x)` yields `convert_eltype(T, x)` for any `x`.
