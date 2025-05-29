```
penultimatedayofyear(dt::TimeType, d::Int) -> TimeType
```

`dt`をその年の前日（最後から2番目の日）に調整します。`d`は曜日を表す整数で、`1 = 月曜日, 2 = 火曜日, &c...`です。

例えば、`penultimatedayofyear(dt, 6)`はその年の前の土曜日を見つけます。日付は整数の別名`月曜日`から`日曜日`をエクスポートしているので、`penultimatedayofyear(dt, Saturday)`と書くこともできます。

関連情報: `Dates.dayofweek`, `lastdayofyear`
