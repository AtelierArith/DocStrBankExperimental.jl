```
advancebdays(calendar, dt, bdays_count) :: Dates.Date
```

Increments given date `dt` by `bdays_count`. Decrements it if `bdays_count` is negative. `bdays_count` can be a `Int`, `Dates.Day`, `Vector{Int}`, `Vector{Dates.Day}` or a `UnitRange`.

Computation starts by next Business Day if `dt` is not a Business Day.
