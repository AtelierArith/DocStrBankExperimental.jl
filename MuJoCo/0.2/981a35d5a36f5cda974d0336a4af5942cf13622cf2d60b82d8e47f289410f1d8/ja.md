```
mj_solveM2(m, d, x, y)
```

線形解の半分:  x = sqrt(inv(D))*inv(L')*y

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`x::Matrix{Float64}`** -> 可変サイズの行列。
  * **`y::Matrix{Float64}`** -> 可変サイズの行列。定数。
