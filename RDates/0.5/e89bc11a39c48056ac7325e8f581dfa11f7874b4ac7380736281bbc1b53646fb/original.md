```
SimpleCalendarManager()
SimpleCalendarManager(calendars::Dict{String, Calendar})
```

A basic calendar manager which just holds a reference to each underlying calendar, by name, and will generate a joint calendar if multiple names are requested.

To set a calendar on this manager then use `setcalendar!`

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcalendar!(mgr, "WEEKEND", WeekendCalendar())
WeekendCalendar()
```

If you want to set a cached wrapping of a calendar then use `setcachedcalendar!`

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcachedcalendar!(mgr, "WEEKEND", WeekendCalendar())
CachedCalendar(WeekendCalendar())
```

### Examples

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcalendar!(mgr, "WEEKEND", WeekendCalendar())
julia> is_holiday(calendar(mgr, ["WEEKEND"]), Date(2019,9,28))
true
```
