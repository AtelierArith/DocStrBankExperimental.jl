```
CFTime.DateTime360Day(y, [m, d, h, mi, s, ms]) -> CFTime.DateTime360Day
```

Construct a `CFTime.DateTime360Day` type by year (`y`), month (`m`, default 1), day (`d`, default 1), hour (`h`, default 0), minute (`mi`, default 0), second (`s`, default 0), millisecond (`ms`, default 0). All arguments must be convertible to `Int64`. `CFTime.DateTime360Day` is a subtype of `AbstractCFDateTime`.

The netCDF CF calendars are defined in [the CF Standard](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar). This type implements the calendar defined as "360day".
