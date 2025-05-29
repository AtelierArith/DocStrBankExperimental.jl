```
mju_cholSolveBand(res, mat, vec, ntotal, nband, ndense)
```

Solve (mat*mat')*res = vec where mat is a band-dense Cholesky factor.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. size of `res` should equal ntotal.
  * **`mat::Vector{Float64}`** -> A vector of variable size. `mat` should be a vector, not a matrix. Constant.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. size of `vec` should equal ntotal. Constant.
  * **`ntotal::Int32`**
  * **`nband::Int32`**
  * **`ndense::Int32`**
