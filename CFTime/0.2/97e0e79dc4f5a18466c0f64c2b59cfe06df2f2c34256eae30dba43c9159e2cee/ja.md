`CFTime`は、気候および予測（CF）netCDF規約に準拠した時間単位をエンコードおよびデコードします。例えば：

```julia
using CFTime, Dates
# "360日"カレンダーのデコード
dt = CFTime.timedecode([0,1,2,3],"days since 2000-01-01 00:00:00",DateTime360Day)
# エンコード
CFTime.timeencode(dt,"days since 2000-01-01 00:00:00",DateTime360Day)
```

サポートされているタイプは `DateTime`、`DateTimeStandard`、`DateTimeJulian`、`DateTimeProlepticGregorian`、`DateTimeAllLeap`、`DateTimeNoLeap` および `DateTime360Day` です。
