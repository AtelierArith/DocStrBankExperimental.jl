```
convert_floating_point_type(T) -> f
```

yields a callable object `f` such that `f(x)` yields `convert_floating_point_type(T, x)` for any `x`.
