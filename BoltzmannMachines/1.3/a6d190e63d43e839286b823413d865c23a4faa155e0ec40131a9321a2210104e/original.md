```
loglikelihood(rbm, x)
loglikelihood(rbm, x, logz)
```

Computes the average log-likelihood of an RBM on a given dataset `x`. Uses `logz` as value for the log of the partition function or estimates the partition function with Annealed Importance Sampling.
