```
Dates.tonext(dt::DateTime, c::Cron; same::Bool = false) -> Union{DateTime, Nothing}
Dates.tonext(t::Time, c::Cron; same::Bool = false) -> Time
Dates.tonext(d::Date, c::Cron; same::Bool = false, limit::Date = d + Day(3000)) -> Union{DateTime, Nothing}
```

Adjust date or time to the next one corresponding to `c::Cron`. Setting `same=true` allows the current date or time to be considered as the next one, allowing for no adjustment to occur.
