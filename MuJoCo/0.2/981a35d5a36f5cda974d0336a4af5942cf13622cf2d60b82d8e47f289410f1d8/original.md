```
mj_solveM2(m, d, x, y)
```

Half of linear solve:  x = sqrt(inv(D))*inv(L')*y

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`x::Matrix{Float64}`** -> A matrix of variable size.
  * **`y::Matrix{Float64}`** -> A matrix of variable size. Constant.
