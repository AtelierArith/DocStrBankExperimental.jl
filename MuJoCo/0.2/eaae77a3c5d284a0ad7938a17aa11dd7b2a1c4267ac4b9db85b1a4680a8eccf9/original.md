```
mju_mulVecMatVec(vec1, mat, vec2)
```

Multiply square matrix with vectors on both sides: returns vec1' * mat * vec2.

# Arguments

  * **`vec1::Vector{Float64}`** -> A vector of variable size. `vec1` should be a vector, not a matrix. Constant.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. Constant.
  * **`vec2::Vector{Float64}`** -> A vector of variable size. `vec2` should be a vector, not a matrix. Constant.
