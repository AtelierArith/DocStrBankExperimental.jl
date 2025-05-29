```
ZonedDateTime(y, [m, d, h, mi, s, ms], tz, [amb]) -> ZonedDateTime
```

Construct a `ZonedDateTime` type by parts. Arguments `y, m, ..., ms` must be convertible to `Int64` and `tz` must be a `TimeZone`. If the given provided local time is ambiguous in the given `TimeZone` then `amb` can be supplied to resolve ambiguity.
