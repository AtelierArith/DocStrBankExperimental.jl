```
mju_mulMatTVec(res, mat, vec)
```

Multiply transposed matrix and vector: res = mat' * vec.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. Constant.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. Constant.
