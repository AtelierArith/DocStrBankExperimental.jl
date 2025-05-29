```
TruncBond{T} <: SVDTrunc
```

A type used to perform SVD-based truncations based on bond size `m'`. Given a vector $\lambda$ of $m$ singular values, only the $m'$ largest are kept, the others are truncated to zero.

# FIELDS

  * `mprime`: number of singular values to retain

```@example
svd_trunc = TruncBond(3)
M = rand(5,6)
M_trunc = svd_trunc(M)
```
