```
expdecay(tau, lags)
```

指数減衰関数を計算します。

# 引数

  * `tau::Real`: タイムスケールパラメータ
  * `lags::AbstractVector`: 時間遅延

# 戻り値

  * exp(-t/tau) の値のベクター

# 注意事項

  * 自己相関関数のフィッティングに使用されます
  * 指数減衰モデルを仮定します: acf = exp(-t/tau)
