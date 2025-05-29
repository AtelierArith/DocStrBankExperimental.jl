`CFTime` encodes and decodes time units conforming to the Climate and Forecasting (CF) netCDF conventions. For example:

```julia
using CFTime, Dates
# Decoding "360 day" calendar
dt = CFTime.timedecode([0,1,2,3],"days since 2000-01-01 00:00:00",DateTime360Day)
# Encoding
CFTime.timeencode(dt,"days since 2000-01-01 00:00:00",DateTime360Day)
```

The following types are supported `DateTime`, `DateTimeStandard`, `DateTimeJulian`, `DateTimeProlepticGregorian` `DateTimeAllLeap`, `DateTimeNoLeap` and `DateTime360Day`
