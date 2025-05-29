```
exactloglikelihood(rbm, x)
```

Computes the mean log-likelihood for the given dataset `x` and the RBM `rbm` exactly. The log of the partition function is computed exactly by `exactlogpartitionfunction(rbm)`. Besides that, the function simply calls `loglikelihood(rbm, x)`.
