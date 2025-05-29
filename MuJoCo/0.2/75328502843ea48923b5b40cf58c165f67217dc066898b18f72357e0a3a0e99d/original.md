```
mj_constraintUpdate(m, d, jar, cost, flg_coneHessian)
```

Compute efc*state, efc*force, qfrc_constraint, and (optionally) cone Hessians. If cost is not NULL, set *cost = s(jar) where jar = Jac*qacc-aref.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`jar::Vector{Float64}`** -> A vector of variable size. `jar` should be a vector, not a matrix. size of `jar` should equal nefc. Constant.
  * **`cost::Vector{Float64}`** -> An **optional** vector of size 1. `cost` should be a vector of size 1. Can set to `nothing` if not required.
  * **`flg_coneHessian::Int32`**
