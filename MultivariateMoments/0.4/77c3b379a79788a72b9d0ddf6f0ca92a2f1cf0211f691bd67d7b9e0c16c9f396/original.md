```
accuracy(chol::LowRankLDLT)
```

Return the ratio `rtol = σ[r+1]/σ[1]` where `σ` is the vector of singular values of the matrix for which `chol` is the rank-`r` Cholesky decomposition. This is a good relative tolerance to use with the matrix as `σ[r+1]` is the first singular value that was discarded.
