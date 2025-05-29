```
TruncThresh{T} <: SVDTrunc
```

A type used to perform SVD-based truncations based on a threshold `ε`. Given a vector $\lambda$ of $m$ singular values, those below $\varepsilon\sqrt{\sum_{k=1}^m \lambda_k^2}$ are truncated to zero.

# FIELDS

  * `ε`: threshold.

```@example
svd_trunc = TruncThresh(1e-5)
M = rand(5,6)
M_trunc = svd_trunc(M)
```
