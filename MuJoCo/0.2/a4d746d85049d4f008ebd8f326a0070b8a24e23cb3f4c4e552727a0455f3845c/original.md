```
mju_mulMatMat(res, mat1, mat2)
```

Multiply matrices: res = mat1 * mat2.

# Arguments

  * **`res::Matrix{Float64}`** -> A matrix of variable size. #rows in `res` should equal #rows in mat1.
  * **`mat1::Matrix{Float64}`** -> A matrix of variable size. #columns in `mat1` should equal #rows in mat2. Constant.
  * **`mat2::Matrix{Float64}`** -> A matrix of variable size. Constant.
