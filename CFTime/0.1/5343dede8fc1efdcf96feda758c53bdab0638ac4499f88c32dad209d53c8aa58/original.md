```
CFTime.DateTimeStandard(y, [m, d, h, mi, s, ms]) -> CFTime.DateTimeStandard
```

Construct a `CFTime.DateTimeStandard` type by year (`y`), month (`m`, default 1), day (`d`, default 1), hour (`h`, default 0), minute (`mi`, default 0), second (`s`, default 0), millisecond (`ms`, default 0). All arguments must be convertible to `Int64`. `CFTime.DateTimeStandard` is a subtype of `AbstractCFDateTime`.

The netCDF CF calendars are defined in [the CF Standard](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar). This type implements the calendar defined as "standard".
