```
mju_addScl(res, vec1, vec2, scl)
```

Set res = vec1 + vec2*scl.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` and vec1 should have the same size. `res` and vec2 should have the same size.
  * **`vec1::Vector{Float64}`** -> A vector of variable size. `vec1` should be a vector, not a matrix. res and `vec1` should have the same size. Constant.
  * **`vec2::Vector{Float64}`** -> A vector of variable size. `vec2` should be a vector, not a matrix. res and `vec2` should have the same size. Constant.
  * **`scl::Float64`**
