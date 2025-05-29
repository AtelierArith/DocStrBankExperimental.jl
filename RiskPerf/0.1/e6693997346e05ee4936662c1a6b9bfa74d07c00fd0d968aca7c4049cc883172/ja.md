```
kurtosis(x; method=:excess)
```

指定された方法を使用して尖度を計算します。

# 方法

  * 超過 (デフォルト)
  * モーメント
  * コーニッシュ-フィッシャー

# 引数

  * `x`:          値のベクトル。
  * `method`:     推定方法: `:excess`, `:moment` または `:cornish_fisher`。
