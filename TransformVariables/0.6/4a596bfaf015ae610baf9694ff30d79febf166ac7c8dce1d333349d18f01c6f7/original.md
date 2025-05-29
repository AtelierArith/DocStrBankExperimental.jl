`transform(t, x)`

Transform `x` using `t`.

`transform(t)`.

Return a callable equivalent to `x -> transform(t, x)` that transforms its argument:

```julia
transform(t, x) == transform(t)(x)
```
