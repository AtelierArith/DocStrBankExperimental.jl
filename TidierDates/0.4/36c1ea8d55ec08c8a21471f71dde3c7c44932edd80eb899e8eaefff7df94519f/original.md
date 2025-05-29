```
ymd_hms(datetime_string::Union{AbstractString, Missing})
```

Convert a string with "Year-Month-Day Hour:Minute:Second" format to a DateTime object.

# Arguments

`datetime_string`: A string (can contain missing values in a DataFrame).

# Returns

A DateTime object converted from the string. If the input is missing or the string format is incorrect, the function returns a missing value.

# Examples

```jldoctest
julia> ymd_hms("2023-06-15 09:30:00")
2023-06-15T09:30:00

julia> ymd_hms("2023/06/15 09:30:00")
2023-06-15T09:30:00

julia> ymd_hms("2023/06/15 09:30:00pm")
2023-06-15T21:30:00

julia> ymd_hms("2023 June 15 09:30:00am")
2023-06-15T09:30:00 

julia> ymd_hms("2023 June 15 09:30:00 P")
2023-06-15T21:30:00

julia> ymd_hms(missing)
missing
```
