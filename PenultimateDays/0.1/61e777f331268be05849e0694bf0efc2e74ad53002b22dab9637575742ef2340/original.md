```
penultimatedayofmonth(dt::TimeType, d::Int) -> TimeType
```

Adjusts `dt` to the penultimate (second-to-last) day of its month, given some `d`, the day of the week as an `Int`, with `1 = Monday, 2 = Tuesday, &c...`

For example, the `penultimatedayofmonth(dt, 6)` will find the penultimate Saturday of the month.  Dates also exports integer aliases `Monday`–`Sunday`, so you can write `penultimatedayofmonth(dt, Saturday)`.

See also: `Dates.dayofweek`, `lastdayofmonth`
