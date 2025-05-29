```
data = timeencode(dt,units,calendar = "standard")
```

指定された単位（例：`"2000-01-01 00:00:00`からの日数"）に従って、`DateTime`（または`DateTimeStandard`、`DateTimeProlepticGregorian`、`DateTimeJulian`、`DateTimeNoLeap`、`DateTimeAllLeap`、`DateTime360Day`）のベクトルまたは配列を変換します。カレンダーは`calendar`を使用します。カレンダーの有効な値は次のとおりです：`"standard"`、`"gregorian"`、`"proleptic_gregorian"`、`"julian"`、`"noleap"`、`"365_day"`、`"all_leap"`、`"366_day"`、`"360_day"`。
