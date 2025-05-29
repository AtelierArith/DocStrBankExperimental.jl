```
mju_sqrMatTD(res, mat, diag)
```

Set res = mat' * diag * mat if diag is not NULL, and res = mat' * mat otherwise.

# Arguments

  * **`res::Matrix{Float64}`** -> A matrix of variable size. #rows in `res` should equal #columns in mat.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. Constant.
  * **`diag::Vector{Float64}`** -> An **optional** vector of variable size. `diag` should be a vector, not a matrix. Can set to `nothing` if not required.
