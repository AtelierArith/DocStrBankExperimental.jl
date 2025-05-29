```
mju_mulMatVec(res, mat, vec)
```

行列とベクトルを掛け算します: res = mat * vec.

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルである必要があり、行列ではありません。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。定数。
  * **`vec::Vector{Float64}`** -> 可変サイズのベクトル。`vec` はベクトルである必要があり、行列ではありません。定数。
