```
logproblowerbound(dbm, x; ...)
logproblowerbound(dbm, x, logimpweights; ...)
logproblowerbound(dbm, x, logz; ...)
```

Estimates the mean of the variational lower bound for the log probability of the DBM on a given dataset `x` like described in Equation 38 in [Salakhutdinov, 2015]. The logarithmized partition function can be specified directly as `logz` or by giving the `logimpweights` from estimating the partition function with the Annealed Importance Sampling algorithm (AIS). (See `aislogimpweights`.) If neither `logimpweights` or `logz` is given, the partition function will be estimated by AIS with default parameters.

# Optional keyword argument:

  * The approximate posterior distribution may be given as argument `mu` or is calculated by the mean-field method.
