```
gridcv_lb(X, Y; segm, algo, score, pars = nothing, lb, verbose = false)
```

Working function for `gridcv`.

Specific and faster than `gridcv_br` for models using ridge regularization (e.g. RR).  Argument `pars` must not contain `nlv`.

See function `gridcv` for examples.
