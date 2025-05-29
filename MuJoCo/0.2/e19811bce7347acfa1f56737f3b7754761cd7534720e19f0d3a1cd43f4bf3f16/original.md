```
mju_mulMatMatT(res, mat1, mat2)
```

Multiply matrices, second argument transposed: res = mat1 * mat2'.

# Arguments

  * **`res::Matrix{Float64}`** -> A matrix of variable size. #rows in `res` should equal #rows in mat1. #columns in `res` should equal #rows in mat2.
  * **`mat1::Matrix{Float64}`** -> A matrix of variable size. Constant.
  * **`mat2::Matrix{Float64}`** -> A matrix of variable size. Constant.
