```
mju_cholSolve(res, mat, vec)
```

Solve (mat*mat') * res = vec, where mat is a Cholesky factor.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should be a square matrix. Constant.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. Constant.
