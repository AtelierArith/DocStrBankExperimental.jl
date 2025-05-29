```
comp_ac_time_missing(data::AbstractArray{T}; kwargs...) where {T <: Real}
```

欠損値を含むデータの自己相関を計算します。

# 引数

  * `data`: 時系列データ（NaNを含む可能性があります）
  * `dims=ndims(data)`: 計算を行う次元
  * `n_lags=size(data,dims)`: 計算するラグの数

# 戻り値

  * 自己相関値の配列

# 注意事項

  * statsmodels.tsa.stattools.acfのmissing="conservative"アプローチを使用して欠損データを処理します。詳細については https://www.statsmodels.org/dev/generated/statsmodels.tsa.stattools.acf.html を参照してください。
