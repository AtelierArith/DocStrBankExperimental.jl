```
supportpoints(Y, npt; maxit_grad=1000, tol_mm=1e-4, verbosity=0, rng=Random.default_rng())
```

Find a set of 'npt' support points that represent the distribution of the values in 'Y', which is a d x n matrix.  The features are in the columns of 'Y'.  The support points are returned as a d x npt matrix.

The default algorithm is up to 'maxit*mm' majorization/maximization iterations, followed by up to 'maxit*grad' gradient descent iterations.
