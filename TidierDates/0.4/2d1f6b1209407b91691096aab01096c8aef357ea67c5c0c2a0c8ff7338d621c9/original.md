```
round_date(dt::Union{DateTime, Date, Time, Missing}, unit::String)
```

Round a DateTime, Date, or Time object to the nearest specified unit.

# Arguments

`dt`: A DateTime, Date, or Time object (can contain missing values in a DataFrame). `unit`: A string specifying the units to use for rounding. The units can be one of the following: "year", "quarter", "month", "day", "hour", "minute", "second".

# Returns

The DateTime, Date, or Time object rounded to the nearest specified unit. If the input is missing, the function returns a missing value.

# Examples

```jldoctest
julia> dt = DateTime(2023, 6, 15, 9, 45)
2023-06-15T09:45:00

julia> round_date(dt, "hour")
2023-06-15T10:00:00

julia> round_date(dt, "day")
2023-06-15T00:00:00

julia> round_date(dt, "quarter")
2023-07-01T00:00:00

julia> round_date(missing, "day")
missing
```
