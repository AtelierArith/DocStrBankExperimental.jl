```
mj_solveM(m, d, x, y)
```

Solve linear system M * x = y using factorization:  x = inv(L'*D*L)*y

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`x::Matrix{Float64}`** -> A matrix of variable size.
  * **`y::Matrix{Float64}`** -> A matrix of variable size. Constant.
