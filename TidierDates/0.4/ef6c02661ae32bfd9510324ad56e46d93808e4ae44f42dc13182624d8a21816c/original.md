```
ymd_hm(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "YYYY-MM-DD HH:MM" to a DateTime object.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed year, month, day, hour, and minute values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> ymd_hm("2023-06-15 09:30")
2023-06-15T09:30:00

julia> ymd_hm("2023-06-15 09:30p")
2023-06-15T21:30:00

julia> ymd_hm(missing)
missing
```
