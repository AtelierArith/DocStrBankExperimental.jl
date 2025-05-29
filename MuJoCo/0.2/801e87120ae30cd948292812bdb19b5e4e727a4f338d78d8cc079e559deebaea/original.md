```
mj_normalizeQuat(m, qpos)
```

Normalize all quaternions in qpos-type vector.

# Arguments

  * **`m::Model`** -> Constant.
  * **`qpos::Vector{Float64}`** -> A vector of variable size. `qpos` should be a vector, not a matrix. `qpos` should be of size nq.
