```
comp_cc(data1::AbstractArray{T}, data2::AbstractArray{T}, max_lag::Integer;
       dims::Int=ndims(data1)) where {T <: Real}
```

2つの配列間のクロス相関を指定された次元に沿って計算します。

# 引数

  * `data1`: 時系列データの最初の配列
  * `data2`: 時系列データの2番目の配列
  * `max_lag`: 計算する最大ラグ
  * `dims`: クロス相関を計算する次元（デフォルトは最後の次元）

# 戻り値

指定された次元に沿って削減されたクロス相関値の配列
