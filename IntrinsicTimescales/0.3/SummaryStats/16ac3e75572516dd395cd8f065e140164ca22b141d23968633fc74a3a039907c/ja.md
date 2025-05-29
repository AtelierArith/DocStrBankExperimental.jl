```
comp_ac_fft(data::AbstractArray{T}; dims::Int=ndims(data), n_lags::Integer=size(data, dims)) where {T <: Real}
```

指定された次元に沿ってFFTを使用して自己相関を計算します。

# 引数

  * `data`: 時系列データの配列
  * `dims`: 自己相関を計算する次元（デフォルトは最後の次元）
  * `n_lags`: 計算するラグの数（デフォルトは指定された次元に沿ったデータのサイズ）

# 戻り値

自己相関値を持つ配列、指定された次元はラグの次元になり、他の次元はACF値を示します。
