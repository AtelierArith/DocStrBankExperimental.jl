```
mju_bandMulMatVec(res, mat, vec, ntotal, nband, ndense, nVec, flg_sym)
```

バンド対角行列とnvecベクトルを掛け算します。flg_sym>0の場合は上三角を含みます。

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res`はベクトルである必要があり、行列ではありません。`res`はntotal行を持つ必要があります。`res`はnVec列を持つ必要があります。
  * **`mat::Matrix{Float64}`** -> 可変サイズの行列。定数です。
  * **`vec::Matrix{Float64}`** -> 可変サイズの行列。`vec`はntotal行を持つ必要があります。`vec`はnVec列を持つ必要があります。定数です。
  * **`ntotal::Int32`** -> `res`は`ntotal`行を持つ必要があります。`vec`は`ntotal`行を持つ必要があります。
  * **`nband::Int32`**
  * **`ndense::Int32`**
  * **`nVec::Int32`** -> `res`は`nVec`列を持つ必要があります。`vec`は`nVec`列を持つ必要があります。
  * **`flg_sym::UInt8`**
