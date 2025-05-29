```
mj_mulM2(m, d, res, vec)
```

Multiply vector by (inertia matrix)^(1/2).

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`** -> Constant.
  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` should be of size nv.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. `vec` should be of size nv. Constant.
