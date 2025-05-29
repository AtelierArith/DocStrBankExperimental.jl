```
mju_cholFactorBand(mat, ntotal, nband, ndense, diagadd, diagmul)
```

Band-dense Cholesky decomposition.  Returns minimum value in the factorized diagonal, or 0 if rank-deficient.  mat has (ntotal-ndense) x nband + ndense x ntotal elements.  The first (ntotal-ndense) x nband store the band part, left of diagonal, inclusive.  The second ndense x ntotal store the band part as entire dense rows.  Add diagadd+diagmul*mat_ii to diagonal before factorization.

# Arguments

  * **`mat::Vector{Float64}`** -> A vector of variable size. `mat` should be a vector, not a matrix.
  * **`ntotal::Int32`**
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`diagadd::Float64`**
  * **`diagmul::Float64`**
