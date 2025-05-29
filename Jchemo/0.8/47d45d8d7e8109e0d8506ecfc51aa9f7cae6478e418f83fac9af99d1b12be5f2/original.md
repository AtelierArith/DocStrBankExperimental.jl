```
gridcv_lv((X, Y; segm, algo, score, pars = nothing, nlv, verbose = false)
```

Working function for `gridcv`.

Specific and faster than `gridcv_br` for models using latent variables (e.g. PLSR).  Argument `pars` must not contain `nlv`.

See function `gridcv` for examples.
