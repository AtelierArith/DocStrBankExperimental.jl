```
penultimatedayofquarter(dt::TimeType, d::Int) -> TimeType
```

`dt`を四半期の前々日（最後から2番目の日）に調整します。`d`は曜日を表す整数で、`1 = 月曜日, 2 = 火曜日, &c...`です。

例えば、`penultimatedayofquarter(dt, 6)`は四半期の前々土曜日を見つけます。日付は整数エイリアス`Monday`–`Sunday`もエクスポートしているので、`penultimatedayofquarter(dt, Saturday)`と書くことができます。

関連情報: `Dates.dayofweek`, `lastdayofquarter`
