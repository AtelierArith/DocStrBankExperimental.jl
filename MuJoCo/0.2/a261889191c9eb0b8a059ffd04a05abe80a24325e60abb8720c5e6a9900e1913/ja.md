```
mju_cholSolve(res, mat, vec)
```

(mat*mat') * res = vec を解きます。ここで、mat はコレスキー因子です。

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルであるべきで、行列ではありません。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。`mat` は正方行列であるべきです。定数。
  * **`vec::Vector{Float64}`** -> 可変サイズのベクトル。`vec` はベクトルであるべきで、行列ではありません。定数。
