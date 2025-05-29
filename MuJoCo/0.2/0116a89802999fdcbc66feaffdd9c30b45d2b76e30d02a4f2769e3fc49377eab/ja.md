```
mju_mulMatTMat(res, mat1, mat2)
```

行列を乗算します。最初の引数は転置されます: res = mat1' * mat2。

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res`の行数はmat1の列数と等しくする必要があります。
  * **`mat1::Matrix{Float64}`** -> 可変サイズの行列。mat1の行数はmat2の行数と等しくする必要があります。定数。
  * **`mat2::Matrix{Float64}`** -> 可変サイズの行列。定数。
