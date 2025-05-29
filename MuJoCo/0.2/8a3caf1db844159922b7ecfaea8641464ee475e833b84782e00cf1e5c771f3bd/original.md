```
mj_applyFT(m, d, force, torque, point, body, qfrc_target)
```

Apply Cartesian force and torque (outside xfrc_applied mechanism).

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`force::Vector{Float64}`** -> A vector of size 3. `force` should be a vector of size 3. Constant.
  * **`torque::Vector{Float64}`** -> A vector of size 3. `torque` should be a vector of size 3. Constant.
  * **`point::Vector{Float64}`** -> A vector of size 3. `point` should be a vector of size 3. Constant.
  * **`body::Int32`**
  * **`qfrc_target::Vector{Float64}`** -> A vector of variable size. `qfrc_target` should be a vector, not a matrix. `qfrc_target` should be of size nv.
