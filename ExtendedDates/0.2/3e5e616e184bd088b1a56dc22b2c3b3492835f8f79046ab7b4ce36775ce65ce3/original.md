```
lastdayofsemester(dt::TimeType) -> TimeType
```

Adjusts `dt` to the last day of its semester.

# Examples

```jldoctest
julia> ExtendedDates.lastdayofsemester(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> ExtendedDates.lastdayofsemester(DateTime("1996-08-20"))
1996-12-31T00:00:00
```
