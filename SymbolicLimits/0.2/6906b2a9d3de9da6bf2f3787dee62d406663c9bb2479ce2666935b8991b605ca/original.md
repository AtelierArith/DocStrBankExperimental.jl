```
limit(expr, var, h[, side::Symbol])
```

Compute the limit of `expr` as `var` approaches `h` and return `(limit, assumptions)`. If all the `assumptions` are true, then the returned `limit` is correct.

`side` indicates the direction from which `var` approaches `h`. It may be one of `:left`, `:right`, or `:both`. If `side` is `:both` and the two sides do not align, an error is thrown. Side defaults to `:both` for finite `h`, `:left` for `h = Inf`, and `:right` for `h = -Inf`.
