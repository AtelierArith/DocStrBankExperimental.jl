```
RateCurve(reference_date::Date, tenors::AbstractVector, dfs::AbstractVector; interp = ...)
```

日付ベースのオーバーロード `RateCurve`。

# 引数

  * `reference_date`: `Date` オブジェクト。
  * `tenors`: 年の分数のベクトル。
  * `dfs`: 割引率。
  * `interp`: 補間器ビルダー。

# 戻り値

  * `RateCurve` インスタンス。
