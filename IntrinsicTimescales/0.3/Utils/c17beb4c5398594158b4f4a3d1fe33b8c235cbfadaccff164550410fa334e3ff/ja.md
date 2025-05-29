```
acw0(lags, acf; dims=ndims(acf))
```

指定された次元に沿ってACW0（ゼロ交差での自己相関幅）を計算します。

# 引数

  * `lags::AbstractVector{T}`: ラグ値のベクトル
  * `acf::AbstractArray{T}`: 自己相関値の配列
  * `dims::Int=ndims(acf)`: ACW0を計算する次元

# 戻り値

  * 自己相関がゼロを越える最初のラグ

# 注意事項

  * 特徴的な時間スケールの代替測定
  * ACW50よりもノイズに敏感
