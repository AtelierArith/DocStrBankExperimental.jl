```
mj_rne(m, d, flg_acc, result)
```

RNE: compute M(qpos)*qacc + C(qpos,qvel); flg_acc=0 removes inertial term.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`flg_acc::Int32`**
  * **`result::Vector{Float64}`** -> A vector of variable size. `result` should be a vector, not a matrix. `result` should have length nv.
