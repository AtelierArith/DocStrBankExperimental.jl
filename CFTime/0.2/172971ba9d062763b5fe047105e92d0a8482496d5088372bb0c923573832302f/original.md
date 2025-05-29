```
CFTime.DateTimeProlepticGregorian([Ti::DataType], y, [m, d, h, mi, s, ms, ...], origin = (1900, 1, 1), units = ...) -> CFTime.DateTimeProlepticGregorian
```

Construct a `CFTime.DateTimeProlepticGregorian` type by year (`y`), month (`m`, default 1), day (`d`, default 1), hour (`h`, default 0), minute (`mi`, default 0), second (`s`, default 0), millisecond (`ms`, default 0), .... Currently `attosecond` is the smallest supported time unit.

All arguments must be convertible to `Int64`. `CFTime.DateTimeProlepticGregorian` is a subtype of `AbstractCFDateTime`.

The date is stored a duration since the time `origin` (epoch) expressed as `milliseconds` but smaller time units will be used if necessary. For example if the user provides 8 integers, they will be interpreted as year, month, day, hour, minute, second, millisecond and microsecond. The internal time units will be microsecond in this case.

The netCDF CF calendars are defined in [the CF Standard](http://cfconventions.org/cf-conventions/cf-conventions.html#calendar). This type implements the calendar defined as "prolepticgregorian".
