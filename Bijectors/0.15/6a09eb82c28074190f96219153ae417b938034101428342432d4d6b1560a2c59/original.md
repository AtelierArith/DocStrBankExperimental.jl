```
with_logabsdet_jacobian!(b, x[, y, logjac])
```

Compute `transform(b, x)` and `logabsdetjac(b, x)`, storing the result in `y` and `logjac`, respetively.

If `y` is not provided, then `x` will be used in its place.

Defaults to calling `with_logabsdet_jacobian(b, x)` and updating `y` and `logjac` with the result.
