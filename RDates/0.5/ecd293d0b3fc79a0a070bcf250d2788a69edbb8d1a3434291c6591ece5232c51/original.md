```
apply(rdate::RDate, date::Dates.Date, calendarmgr::CalendarManager)::Dates.Date
```

The application of an rdate to a specific date, given an explicit calendar manager.

### Examples

```jula-repl
julia> cal_mgr = SimpleCalendarManager()
julia> setcalendar!(cal_mgr, "WEEKEND", WeekendCalendar())
julia> apply(rd"1b@WEEKEND", Date(2021,7,9), cal_mgr)
2021-07-12
```
