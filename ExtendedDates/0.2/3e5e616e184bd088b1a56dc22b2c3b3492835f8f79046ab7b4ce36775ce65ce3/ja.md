```
lastdayofsemester(dt::TimeType) -> TimeType
```

`dt`をその学期の最終日に調整します。

# 例

```jldoctest
julia> ExtendedDates.lastdayofsemester(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> ExtendedDates.lastdayofsemester(DateTime("1996-08-20"))
1996-12-31T00:00:00
```
