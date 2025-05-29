```
mju_cholFactor(mat, mindiag)
```

Cholesky decomposition: mat = L*L'; return rank, decomposition performed in-place into mat.

# Arguments

  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should be a square matrix.
  * **`mindiag::Float64`**
