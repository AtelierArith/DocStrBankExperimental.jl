```
mj_mulJacVec(m, d, res, vec)
```

Multiply dense or sparse constraint Jacobian by vector.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` should be of length nefc.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. `vec` should be of length nv. Constant.
