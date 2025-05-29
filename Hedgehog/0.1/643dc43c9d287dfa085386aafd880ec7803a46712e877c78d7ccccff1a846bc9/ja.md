```
RateCurve(reference_date::Date, itp::I, builder::F) where {I, F}
```

`RateCurve`を事前に構築された補間コンポーネントと`Date`から構築します。

# 引数

  * `reference_date`: 曲線の日付。
  * `itp`: `DataInterpolations.AbstractInterpolation`オブジェクト。
  * `builder`: 補間器再構築関数。

# 戻り値

  * `RateCurve`インスタンス。
