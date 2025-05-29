```
ZonedDateTime(dt::DateTime, tz::VariableTimeZone, is_dst::Bool) -> ZonedDateTime
```

`DateTime`に`TimeZone`を適用することで`ZonedDateTime`を構築します。指定されたタイムゾーン内で`DateTime`が曖昧な場合は、`is_dst`を設定して曖昧さを解消できます。
