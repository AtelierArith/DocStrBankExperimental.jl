```
acw_romberg(lags, acf)
```

ACFの下の面積をロムバーグ積分を使用して計算します。

# 引数

  * `dt::Real`: 時間ステップ
  * `acf::AbstractVector`: 自己相関値の配列

# 戻り値

  * ACFのAUC

# 注意事項

  * エラー推定を破棄して、積分値のみを返します。
