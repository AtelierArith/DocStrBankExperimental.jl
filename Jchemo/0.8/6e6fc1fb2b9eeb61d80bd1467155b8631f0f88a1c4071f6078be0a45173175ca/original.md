```
gridscore_lb(Xtrain, Ytrain, X, Y; algo, score, pars = nothing, 
    lb, verbose = false)
```

Working function for `gridscore`.

Specific and faster than `gridscore_br` for models using ridge regularization (e.g. RR).  Argument `pars` must not contain `lb`.

See function `gridscore` for examples.
