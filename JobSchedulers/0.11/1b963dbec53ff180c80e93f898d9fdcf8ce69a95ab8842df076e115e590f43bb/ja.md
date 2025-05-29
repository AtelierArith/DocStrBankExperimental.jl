```
Dates.tonext(dt::DateTime, c::Cron; same::Bool = false) -> Union{DateTime, Nothing}
Dates.tonext(t::Time, c::Cron; same::Bool = false) -> Time
Dates.tonext(d::Date, c::Cron; same::Bool = false, limit::Date = d + Day(3000)) -> Union{DateTime, Nothing}
```

`c::Cron`に対応する次の日付または時間に調整します。`same=true`を設定すると、現在の日付または時間を次のものとして考慮でき、調整が行われないようになります。
