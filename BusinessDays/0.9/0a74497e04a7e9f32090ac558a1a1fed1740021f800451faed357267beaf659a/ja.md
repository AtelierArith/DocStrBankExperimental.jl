```
advancebdays(calendar, dt, bdays_count) :: Dates.Date
```

指定された日付 `dt` を `bdays_count` だけ進めます。`bdays_count` が負の場合は減少させます。`bdays_count` は `Int`、`Dates.Day`、`Vector{Int}`、`Vector{Dates.Day}` または `UnitRange` であることができます。

計算は、`dt` が営業日でない場合、次の営業日から始まります。
