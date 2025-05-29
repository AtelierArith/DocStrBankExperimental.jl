```
penultimatedayofyear(dt::TimeType, d::Int) -> TimeType
```

Adjusts `dt` to the penultimate (second-to-last) day of its year, given some `d`, the day of the week as an `Int`, with `1 = Monday, 2 = Tuesday, &c...`

For example, the `penultimatedayofyear(dt, 6)` will find the penultimate Saturday of the year.  Dates also exports integer aliases `Monday`–`Sunday`, so you can write `penultimatedayofyear(dt, Saturday)`.

See also: `Dates.dayofweek`, `lastdayofyear`
