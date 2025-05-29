```
dt = timedecode(data,units,calendar = "standard"; prefer_datetime = true)
```

データ内の時間情報を、指定されたカレンダーに従って、単位 `units` によって与えられた通りにデコードします。`calendar` に対して有効な値は `"standard"`、`"gregorian"`、`"proleptic_gregorian"`、`"julian"`、`"noleap"`、`"365_day"`、`"all_leap"`、`"366_day"` および `"360_day"` です。

`prefer_datetime` が `true`（デフォルト）の場合、日付は `DateTime` 型に変換されます（カレンダーが "standard"、"gregorian"、"proleptic_gregorian" および "julian" の場合）、ただし時間単位がマイクロ秒以下で表現されている場合は除きます。他のカレンダーに対しては、そのような変換は不可能です。

|                   カレンダー | 型 (prefer_datetime=true) |    型 (prefer_datetime=false) |
| -----------------------:| ------------------------:| ----------------------------:|
| `standard`, `gregorian` |               `DateTime` |           `DateTimeStandard` |
|   `proleptic_gregorian` |               `DateTime` | `DateTimeProlepticGregorian` |
|                `julian` |               `DateTime` |             `DateTimeJulian` |
|     `noleap`, `365_day` |         `DateTimeNoLeap` |             `DateTimeNoLeap` |
|   `all_leap`, `366_day` |        `DateTimeAllLeap` |            `DateTimeAllLeap` |
|               `360_day` |         `DateTime360Day` |             `DateTime360Day` |

## 例:

```julia
using CFTime, Dates
# 標準カレンダー
dt = CFTime.timedecode([0,1,2,3],"days since 2000-01-01 00:00:00")
# 4-element Array{Dates.DateTime,1}:
#  2000-01-01T00:00:00
#  2000-01-02T00:00:00
#  2000-01-03T00:00:00
#  2000-01-04T00:00:00

dt = CFTime.timedecode([0,1,2,3],"days since 2000-01-01 00:00:00","360_day")
# 4-element Array{DateTime360Day,1}:
#  DateTime360Day(2000-01-01T00:00:00)
#  DateTime360Day(2000-01-02T00:00:00)
#  DateTime360Day(2000-01-03T00:00:00)
#  DateTime360Day(2000-01-04T00:00:00)
```
