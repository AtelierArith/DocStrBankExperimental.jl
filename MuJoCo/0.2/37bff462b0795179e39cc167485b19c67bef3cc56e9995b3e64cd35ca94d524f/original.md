```
mju_bandMulMatVec(res, mat, vec, ntotal, nband, ndense, nVec, flg_sym)
```

Multiply band-diagonal matrix with nvec vectors, include upper triangle if flg_sym>0.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` should have ntotal rows. `res` should have nVec columns.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. Constant.
  * **`vec::Matrix{Float64}`** -> A matrix of variable size. `vec` should have ntotal rows. `vec` should have nVec columns. Constant.
  * **`ntotal::Int32`** -> res should have `ntotal` rows. vec should have `ntotal` rows.
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`nVec::Int32`** -> res should have `nVec` columns. vec should have `nVec` columns.
  * **`flg_sym::UInt8`**
