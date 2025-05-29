```
fit_expdecay(lags, acf; dims=ndims(acf))
```

自己相関関数に指数減衰をフィットします。

# 引数

  * `lags::AbstractVector{T}`: 時間遅れ
  * `acf::AbstractArray{T}`: 自己相関値
  * `dims::Int=ndims(acf)`: フィットする次元

# 戻り値

  * フィットされた時間スケールパラメータ

# 注意事項

  * NonlinearSolve.jlをFastShortcutNLLSPolyalgと共に使用
  * 初期推定はACW50に基づく
