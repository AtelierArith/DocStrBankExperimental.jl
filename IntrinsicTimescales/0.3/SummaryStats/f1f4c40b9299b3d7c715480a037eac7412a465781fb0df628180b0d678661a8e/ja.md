```
comp_ac_time(data::AbstractArray{T}, max_lag::Integer; dims::Int=ndims(data)) where {T <: Real}
```

指定された次元に沿った時間領域での自己相関を計算します。

# 引数

  * `data`: 時系列データの配列
  * `max_lag`: 計算する最大ラグ
  * `dims`: 自己相関を計算する次元（デフォルトは最後の次元）

# 戻り値

自己相関値を持つ配列で、指定された次元がラグの次元になり、他の次元がACF値を示します。
