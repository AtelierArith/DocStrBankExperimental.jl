```
data = timeencode(dt,units,calendar = "standard")
```

Convert a vector or array of `DateTime` (or `DateTimeStandard`, `DateTimeProlepticGregorian`, `DateTimeJulian`, `DateTimeNoLeap`, `DateTimeAllLeap`, `DateTime360Day`) according to the specified units (e.g. `"days since 2000-01-01 00:00:00"`) using the calendar `calendar`.  Valid values for calendar are: `"standard"`, `"gregorian"`, `"proleptic_gregorian"`, `"julian"`, `"noleap"`, `"365_day"`, `"all_leap"`, `"366_day"`, `"360_day"`.
