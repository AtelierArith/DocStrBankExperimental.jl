```
ZonedDateTime(dt::DateTime, tz::VariableTimeZone, occurrence::Integer) -> ZonedDateTime
```

Construct a `ZonedDateTime` by applying a `TimeZone` to a `DateTime`. If the `DateTime` is ambiguous within the given time zone you can set `occurrence` to a positive integer to resolve the ambiguity.
