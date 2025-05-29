```
mju_band2Dense(res, mat, ntotal, nband, ndense, flg_sym)
```

Convert banded matrix to dense matrix, fill upper triangle if flg_sym>0.

# Arguments

  * **`res::Matrix{Float64}`** -> A matrix of variable size. `res` should have ntotal rows. `res` should have ntotal columns.
  * **`mat::Vector{Float64}`** -> A vector of variable size. `mat` should be a vector, not a matrix. Constant.
  * **`ntotal::Int32`** -> res should have `ntotal` rows. res should have `ntotal` columns.
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`flg_sym::UInt8`**
