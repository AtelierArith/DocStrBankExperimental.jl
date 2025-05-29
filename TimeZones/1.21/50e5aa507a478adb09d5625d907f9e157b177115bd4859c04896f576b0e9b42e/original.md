```
ZonedDateTime(dt::DateTime, tz::TimeZone; from_utc=false) -> ZonedDateTime
```

Construct a `ZonedDateTime` by applying a `TimeZone` to a `DateTime`. When the `from_utc` keyword is true the given `DateTime` is assumed to be in UTC instead of in local time and is converted to the specified `TimeZone`.  Note that when `from_utc` is true the given `DateTime` will always exists and is never ambiguous.
