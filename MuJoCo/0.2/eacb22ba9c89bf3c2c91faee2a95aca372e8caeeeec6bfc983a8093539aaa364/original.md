```
mj_jacBody(m, d, jacp, jacr, body)
```

Compute body frame end-effector Jacobian.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`jacp::Matrix{Float64}`** -> An **optional** matrix of variable size. `jacp` should be of shape (3, nv). Can set to `nothing` if not required.
  * **`jacr::Matrix{Float64}`** -> An **optional** matrix of variable size. `jacr` should be of shape (3, nv). Can set to `nothing` if not required.
  * **`body::Int32`**
