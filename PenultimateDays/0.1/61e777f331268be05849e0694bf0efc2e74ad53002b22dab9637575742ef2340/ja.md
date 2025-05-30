```
penultimatedayofmonth(dt::TimeType, d::Int) -> TimeType
```

`dt`をその月の前日（最後から2番目の日）に調整します。`d`は曜日を表す整数で、`1 = 月曜日, 2 = 火曜日, &c...`です。

例えば、`penultimatedayofmonth(dt, 6)`はその月の前の土曜日を見つけます。日付は整数のエイリアス`月曜日`から`日曜日`をエクスポートしているので、`penultimatedayofmonth(dt, Saturday)`と書くこともできます。

関連情報: `Dates.dayofweek`, `lastdayofmonth`
