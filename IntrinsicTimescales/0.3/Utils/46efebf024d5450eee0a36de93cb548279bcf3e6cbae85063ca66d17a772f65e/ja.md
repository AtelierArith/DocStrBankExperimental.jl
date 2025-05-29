```
acweuler(lags, acf; dims=ndims(acf))
```

指定された次元に沿って1/e (≈ 0.368) でのACWを計算します。

# 引数

  * `lags::AbstractVector{T}`: ラグ値のベクトル
  * `acf::AbstractArray{S}`: 自己相関値の配列
  * `dims::Int=ndims(acf)`: 計算を行う次元

# 戻り値

  * 自己相関が1/eを下回る最初のラグ

# 注意事項

  * 指数的減衰の場合、タイムスケールパラメータtauに等しいです。
