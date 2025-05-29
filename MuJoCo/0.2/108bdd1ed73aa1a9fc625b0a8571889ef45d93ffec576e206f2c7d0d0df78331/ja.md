```
mju_band2Dense(res, mat, ntotal, nband, ndense, flg_sym)
```

バンド行列を密行列に変換し、flg_sym>0の場合は上三角を埋めます。

# 引数

  * **`res::Matrix{Float64}`** -> 可変サイズの行列。`res`はntotal行を持つ必要があります。`res`はntotal列を持つ必要があります。
  * **`mat::Vector{Float64}`** -> 可変サイズのベクトル。`mat`はベクトルである必要があり、行列ではありません。定数。
  * **`ntotal::Int32`** -> `res`は`ntotal`行を持つ必要があります。`res`は`ntotal`列を持つ必要があります。
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`flg_sym::UInt8`**
