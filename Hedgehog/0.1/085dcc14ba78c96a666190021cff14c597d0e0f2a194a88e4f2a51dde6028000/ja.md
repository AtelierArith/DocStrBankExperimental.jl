```
FlatRateCurve(rate::Number; reference_date::TimeType = Date(0))
```

一定のゼロレートを持つフラットカーブを作成します。

# 引数

  * `rate`: 一定の連続複利レート。
  * `reference_date`: 参照日（デフォルトはJuliaエポック）。

# 戻り値

  * `FlatRateCurve`インスタンス。
