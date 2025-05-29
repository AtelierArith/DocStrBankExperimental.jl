```
nrmse(x, y) → e
```

Return the normalized root mean square error of the "fit" `y` into data `x`. This number is the relative error of `y` to `x` versus `mean(x)` to `x`, i.e. if `e < 1` the fit `y` is better than using `mean(x)` as a fit.
