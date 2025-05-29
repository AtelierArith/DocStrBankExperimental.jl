```
exactloglikelihood(dbm, x)
exactloglikelihood(dbm, x, logz)
```

Computes the mean log-likelihood for the given dataset `x` and the DBM `dbm` exactly. If the value of the log of the partition function of the `dbm` is not supplied as argument `logz`, it will be computed by `exactlogpartitionfunction(dbm)`.
