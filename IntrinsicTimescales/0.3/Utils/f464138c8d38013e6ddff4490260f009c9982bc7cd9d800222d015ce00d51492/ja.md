```
acw50(lags, acf; dims=ndims(acf))
```

指定された次元に沿ってACW50（50％での自己相関幅）を計算します。

# 引数

  * `lags::AbstractVector{T}`: ラグ値のベクトル
  * `acf::AbstractArray{T}`: 自己相関値の配列
  * `dims::Int=ndims(acf)`: ACW50を計算する次元

# 戻り値

  * 自己相関が0.5を下回る最初のラグ

# 注意事項

  * 特徴的な時間スケールを推定するために使用されます
  * τに関連して: τ = -acw50/log(0.5)
