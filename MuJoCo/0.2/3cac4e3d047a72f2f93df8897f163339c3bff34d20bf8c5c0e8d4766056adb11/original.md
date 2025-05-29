```
mj_jacPointAxis(m, d, jacp, jacr, point, axis, body)
```

Compute translation end-effector Jacobian of point, and rotation Jacobian of axis.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`jacp::Matrix{Float64}`** -> An **optional** matrix of variable size. `jacp` should be of shape (3, nv). Can set to `nothing` if not required.
  * **`jacr::Matrix{Float64}`** -> An **optional** matrix of variable size. `jacr` should be of shape (3, nv). Can set to `nothing` if not required.
  * **`point::Vector{Float64}`** -> A vector of size 3. `point` should be a vector of size 3. Constant.
  * **`axis::Vector{Float64}`** -> A vector of size 3. `axis` should be a vector of size 3. Constant.
  * **`body::Int32`**
