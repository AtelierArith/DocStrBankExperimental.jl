```
FlatRateCurve{R <: Number, S <: Number} <: AbstractRateCurve
```

一定の連続複利ゼロレートを持つフラットカーブを表します。

# フィールド

  * `reference_date::R`: カーブの基準日、内部ティック単位で。
  * `rate::S`: すべてのテナーに適用される一定のゼロレート。
