```
ZonedDateTime(y, [m, d, h, mi, s, ms], tz, [amb]) -> ZonedDateTime
```

部分から `ZonedDateTime` 型を構築します。引数 `y, m, ..., ms` は `Int64` に変換可能でなければならず、`tz` は `TimeZone` でなければなりません。指定されたローカル時間が与えられた `TimeZone` であいまいな場合、あいまいさを解決するために `amb` を提供することができます。
