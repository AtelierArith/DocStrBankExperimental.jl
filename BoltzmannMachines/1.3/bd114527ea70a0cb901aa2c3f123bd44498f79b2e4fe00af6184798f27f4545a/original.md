```
meanfield(dbm, x)
meanfield(dbm, x, eps)
```

Computes the mean-field approximation for the data set `x` and returns a matrix of particles for the DBM. The number of particles is equal to the number of samples in `x`. `eps` is the convergence criterion for the fix-point iteration, default 0.001. It is assumed that all nodes in in-between-layers are Bernoulli distributed.
