```
tensorMixedMomentSystem(d, k, mixing, ms, vs)
```

Build a linear system for finding the off-diagonal covariances entries using tensor moments.

For a `d` dimensional Gaussian `k`-mixture model with mixing coefficients `mixing`, means `ms`, and covariances `vs` where the diagonal entries have been filled in and the off diagonals are variables.
