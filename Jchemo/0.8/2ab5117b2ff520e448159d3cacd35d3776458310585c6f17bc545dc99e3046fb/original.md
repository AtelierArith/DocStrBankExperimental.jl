```
gridscore_lv(Xtrain, Ytrain, X, Y; algo, score, pars = nothing, 
    nlv, verbose = false)
```

Working function for `gridscore`.

Specific and faster than `gridscore_br` for models using latent variables (e.g. PLSR).  Argument `pars` must not contain `nlv`.

See function `gridscore` for examples.
