```
mj_differentiatePos(m, qvel, dt, qpos1, qpos2)
```

Compute velocity by finite-differencing two positions.

# Arguments

  * **`m::Model`** -> Constant.
  * **`qvel::Vector{Float64}`** -> A vector of variable size. `qvel` should be a vector, not a matrix. `qvel` should be of size nv.
  * **`dt::Float64`**
  * **`qpos1::Vector{Float64}`** -> A vector of variable size. `qpos1` should be a vector, not a matrix. `qpos1` should be of size nq. Constant.
  * **`qpos2::Vector{Float64}`** -> A vector of variable size. `qpos2` should be a vector, not a matrix. `qpos2` should be of size nq. Constant.
