```
apply(rdate::RDate, date::Dates.Date, calendarmgr::CalendarManager)::Dates.Date
```

特定の日付に対してrdateを適用する、明示的なカレンダーマネージャーが与えられた場合。

### 例

```jula-repl
julia> cal_mgr = SimpleCalendarManager()
julia> setcalendar!(cal_mgr, "WEEKEND", WeekendCalendar())
julia> apply(rd"1b@WEEKEND", Date(2021,7,9), cal_mgr)
2021-07-12
```
