```
mju_dense2Band(res, mat, ntotal, nband, ndense)
```

密行列をバンド行列に変換します。

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルである必要があります。行列ではありません。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。`mat` は ntotal 行を持つ必要があります。`mat` は ntotal 列を持つ必要があります。定数です。
  * **`ntotal::Int32`** -> mat は `ntotal` 行を持つ必要があります。mat は `ntotal` 列を持つ必要があります。
  * **`nband::Int32`**
  * **`ndense::Int32`**
