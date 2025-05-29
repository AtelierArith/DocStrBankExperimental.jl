```
SinkhornStabilized(; absorb_tol::Real=1_000)
```

Construct a log-domain stabilized Sinkhorn algorithm with absorption tolerance `absorb_tol` for solving an entropically regularized optimal transport problem.

# References

Schmitzer, B. (2019). [Stabilized Sparse Scaling Algorithms for Entropy Regularized Transport Problems](https://doi.org/10.1137/16m1106018). SIAM Journal on Scientific Computing, 41(3), A1443–A1481.
