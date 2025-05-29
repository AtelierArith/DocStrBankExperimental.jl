```
mju_mulMatMat(res, mat1, mat2)
```

行列を掛け算します: res = mat1 * mat2。

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res`の行数はmat1の行数と等しくなければなりません。
  * **`mat1::Matrix{Float64}`** -> 可変サイズの行列。`mat1`の列数はmat2の行数と等しくなければなりません。定数。
  * **`mat2::Matrix{Float64}`** -> 可変サイズの行列。定数。
