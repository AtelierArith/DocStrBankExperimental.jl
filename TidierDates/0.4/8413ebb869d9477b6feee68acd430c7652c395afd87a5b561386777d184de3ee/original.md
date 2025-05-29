```
ymd_h(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "YYYY-MM-DD HH" to a DateTime object. 

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed year, month, day, and hour values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> ymd_h("2023-06-15 09hr")
2023-06-15T09:00:00

julia> ymd_h("2023-06-15 09hr p")
2023-06-15T21:00:00

julia> ymd_h(missing)
missing
```
