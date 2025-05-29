```
penultimatedayofquarter(dt::TimeType, d::Int) -> TimeType
```

Adjusts `dt` to the penultimate (second-to-last) day of its quarter, given some `d`, the day of the week as an `Int`, with `1 = Monday, 2 = Tuesday, &c...`

For example, the `penultimatedayofquarter(dt, 6)` will find the penultimate Saturday of the quarter.  Dates also exports integer aliases `Monday`–`Sunday`, so you can write `penultimatedayofquarter(dt, Saturday)`.

See also: `Dates.dayofweek`, `lastdayofquarter`
