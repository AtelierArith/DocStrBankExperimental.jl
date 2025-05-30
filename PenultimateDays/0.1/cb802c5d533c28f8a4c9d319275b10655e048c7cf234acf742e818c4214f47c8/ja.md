```
penultimatedayofquarter(dt::TimeType, d::Int) -> TimeType
```

`dt`を四半期の前日（第二の最後の日）に調整します。`d`は曜日を表す整数で、`1 = 月曜日, 2 = 火曜日, &c...`です。

例えば、`penultimatedayofquarter(dt, 6)`は四半期の前の土曜日を見つけます。日付は整数のエイリアス`Monday`–`Sunday`もエクスポートしているので、`penultimatedayofquarter(dt, Saturday)`と書くことができます。

参照: `Dates.dayofweek`, `lastdayofquarter`
