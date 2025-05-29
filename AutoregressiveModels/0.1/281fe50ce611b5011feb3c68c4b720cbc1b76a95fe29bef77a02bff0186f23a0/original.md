```
coef(r::VectorAutoregression, yid, xid, lag::Integer=1)
```

Return the coefficient estimate of `r` for variable `yid` with respect to variable `xid` with lag `lag`. `yid` and `xid` can be variable names of type `Symbol` or integer indices. Unless `var.nocons` is `true`, the intercept term is always named `:constant` and has an index of `1`.
