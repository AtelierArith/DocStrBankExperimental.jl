```
mj_mulJacTVec(m, d, res, vec)
```

Multiply dense or sparse constraint Jacobian transpose by vector.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` should be of length nv.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. `vec` should be of length nefc. Constant.
