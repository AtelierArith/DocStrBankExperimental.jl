```
mju_dense2Band(res, mat, ntotal, nband, ndense)
```

Convert dense matrix to banded matrix.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should have ntotal rows. `mat` should have ntotal columns. Constant.
  * **`ntotal::Int32`** -> mat should have `ntotal` rows. mat should have `ntotal` columns.
  * **`nband::Int32`**
  * **`ndense::Int32`**
