```
SimpleCalendarManager()
SimpleCalendarManager(calendars::Dict{String, Calendar})
```

基本的なカレンダーマネージャーで、名前によって各基盤カレンダーへの参照を保持し、複数の名前が要求された場合には共同カレンダーを生成します。

このマネージャーにカレンダーを設定するには、`setcalendar!`を使用します。

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcalendar!(mgr, "WEEKEND", WeekendCalendar())
WeekendCalendar()
```

カレンダーのキャッシュラッピングを設定したい場合は、`setcachedcalendar!`を使用します。

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcachedcalendar!(mgr, "WEEKEND", WeekendCalendar())
CachedCalendar(WeekendCalendar())
```

### 例

```julia-repl
julia> mgr = SimpleCalendarManager()
julia> setcalendar!(mgr, "WEEKEND", WeekendCalendar())
julia> is_holiday(calendar(mgr, ["WEEKEND"]), Date(2019,9,28))
true
```
