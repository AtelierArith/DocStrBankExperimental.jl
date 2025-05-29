```
firstdayofsemester(dt::TimeType) -> TimeType
```

`dt`をその学期の最初の日に調整します。

# 例

```jldoctest
julia> ExtendedDates.firstdayofsemester(DateTime("1996-05-20"))
1996-01-01T00:00:00

julia> ExtendedDates.firstdayofsemester(DateTime("1996-08-20"))
1996-07-01T00:00:00
```
