```
set_datetime_ydh!(df, timezone = tz"UTC+0"; 
    year = df.year, doy = df.doy, hour = df.hour)
```

年、年の最初の日、そして小数時間に従って日付時刻列を更新します。

# 値

更新または追加された列 `:datetime` を最初の位置に移動した `df`。
