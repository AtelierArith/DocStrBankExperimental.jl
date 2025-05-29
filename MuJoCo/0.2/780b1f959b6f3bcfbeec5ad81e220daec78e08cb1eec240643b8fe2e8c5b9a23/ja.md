```
mju_cholSolveBand(res, mat, vec, ntotal, nband, ndense)
```

(mat*mat')*res = vec を解きます。ここで、mat はバンド密なコレスキー因子です。

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルであるべきで、行列ではありません。`res` のサイズは ntotal と等しい必要があります。
  * **`mat::Vector{Float64}`** -> 可変サイズのベクトル。`mat` はベクトルであるべきで、行列ではありません。定数です。
  * **`vec::Vector{Float64}`** -> 可変サイズのベクトル。`vec` はベクトルであるべきで、行列ではありません。`vec` のサイズは ntotal と等しい必要があります。定数です。
  * **`ntotal::Int32`**
  * **`nband::Int32`**
  * **`ndense::Int32`**
