```
convert_bare_type(T) -> f
```

yields a callable object `f` such that `f(x)` yields `convert_bare_type(T, x)` for any `x`.
