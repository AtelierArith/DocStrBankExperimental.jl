```
centred_moving_average(X::Union{FloatMatrix, JMatrix{Float64}}, n::Int64, T::Int64, window::Int64)
```

`X`の中心移動平均を計算します。

# 引数

  * `X`: 観測された測定値 (`nxT`)
  * `n` と `T` は系列数と観測数
  * `window` は平均に含まれる観測値の総数（遅れ、現在、先行）です。
