```
dt = timedecode(data,units,calendar = "standard"; prefer_datetime = true)
```

Decode the time information in data as given by the units `units` according to the specified calendar. Valid values for `calendar` are `"standard"`, `"gregorian"`, `"proleptic_gregorian"`, `"julian"`, `"noleap"`, `"365_day"`, `"all_leap"`, `"366_day"` and `"360_day"`.

If `prefer_datetime` is `true` (default), dates are converted to the `DateTime` type (for the calendars "standard", "gregorian", "proleptic_gregorian" and "julian") unless the time unit is expressed in microseconds or smaller. Such conversion is not possible for the other calendars.

|                Calendar | Type (prefer_datetime=true) | Type (prefer_datetime=false) |
| -----------------------:| ---------------------------:| ----------------------------:|
| `standard`, `gregorian` |                  `DateTime` |           `DateTimeStandard` |
|   `proleptic_gregorian` |                  `DateTime` | `DateTimeProlepticGregorian` |
|                `julian` |                  `DateTime` |             `DateTimeJulian` |
|     `noleap`, `365_day` |            `DateTimeNoLeap` |             `DateTimeNoLeap` |
|   `all_leap`, `366_day` |           `DateTimeAllLeap` |            `DateTimeAllLeap` |
|               `360_day` |            `DateTime360Day` |             `DateTime360Day` |

## Example:

```julia
using CFTime, Dates
# standard calendar
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
