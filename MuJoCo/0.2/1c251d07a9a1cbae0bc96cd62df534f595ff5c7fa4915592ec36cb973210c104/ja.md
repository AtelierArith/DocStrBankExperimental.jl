```
mju_transpose(res, mat)
```

行列の転置: res = mat'.

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res`の列数はmatの行数と等しくなければなりません。`res`の行数はmatの列数と等しくなければなりません。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。定数。
