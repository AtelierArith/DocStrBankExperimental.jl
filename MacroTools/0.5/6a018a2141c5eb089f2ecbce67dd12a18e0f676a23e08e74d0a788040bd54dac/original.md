```
inexpr(expr, x)
```

Simple expression match; will return `true` if the expression `x` can be found inside `expr`.

```julia
inexpr(:(2+2), 2) == true
```
