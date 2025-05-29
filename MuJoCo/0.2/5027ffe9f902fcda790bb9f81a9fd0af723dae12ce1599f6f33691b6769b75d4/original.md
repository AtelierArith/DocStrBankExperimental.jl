```
mju_addToScl(res, vec, scl)
```

Set res = res + vec*scl.

# Arguments

  * **`res::Vector{Float64}`** -> A vector of variable size. `res` should be a vector, not a matrix. `res` and vec should have the same size.
  * **`vec::Vector{Float64}`** -> A vector of variable size. `vec` should be a vector, not a matrix. res and `vec` should have the same size. Constant.
  * **`scl::Float64`**
