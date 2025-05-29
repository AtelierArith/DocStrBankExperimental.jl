```
ZonedDateTime(dt::DateTime, tz::VariableTimeZone, occurrence::Integer) -> ZonedDateTime
```

`DateTime`に`TimeZone`を適用することで`ZonedDateTime`を構築します。指定されたタイムゾーン内で`DateTime`が曖昧な場合は、曖昧さを解消するために`occurrence`を正の整数に設定できます。
