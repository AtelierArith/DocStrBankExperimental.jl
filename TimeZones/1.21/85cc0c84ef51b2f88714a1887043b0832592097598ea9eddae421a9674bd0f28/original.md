```
ZonedDateTime(dt::DateTime, tz::VariableTimeZone, is_dst::Bool) -> ZonedDateTime
```

Construct a `ZonedDateTime` by applying a `TimeZone` to a `DateTime`. If the `DateTime` is ambiguous within the given time zone you can set `is_dst` to resolve the ambiguity.
