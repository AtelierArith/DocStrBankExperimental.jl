```
partial_year(period::Type{<:Period}, float)
```

浮動小数点の年値に基づいて部分年の日付を計算します。

# 引数

  * `period::Type{<:Period}`: 使用する期間のタイプ（例：`Month`、`Day`）。
  * `float::Float64`: 浮動小数点の年値。

# 戻り値

  * `Date`: 部分年に対応する計算された日付。
