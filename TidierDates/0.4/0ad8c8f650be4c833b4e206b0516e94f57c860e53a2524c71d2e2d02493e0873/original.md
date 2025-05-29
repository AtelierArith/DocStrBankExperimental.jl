```
floor_date(dt::Union{DateTime, Missing}, unit::String)
```

Round down a DateTime object to the nearest specified unit.

# Arguments

`dt`: A DateTime object (can contain missing values in a DataFrame). `unit`: A string specifying the units to use for rounding down. The units can be one of the following: "year", "quarter", "month", "week", "day", "hour", "minute".

# Returns

The DateTime object rounded down to the nearest specified unit. If the input is missing, the function returns a missing value.

When using the "week" unit, Sunday is considered the first day of the week, and if the date is already a Sunday, it is returned as is.

# Examples

```jldoctest
julia> dt = DateTime(2023, 6, 15, 9, 45)
2023-06-15T09:45:00

julia> floor_date(dt, "hour")
2023-06-15T09:00:00

julia> floor_date(dt, "day")
2023-06-15T00:00:00

julia> floor_date(dt, "week")
2023-06-11T00:00:00

julia> floor_date(dt, "quarter")
2023-04-01T00:00:00

julia> floor_date(missing, "day")
missing
```
