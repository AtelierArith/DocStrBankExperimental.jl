```
mdy_hms(datetime_string::Union{AbstractString, Missing})
```

Parses a datetime string that is expected to contain month, day, year, hour, minute, and second values.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed month, day, year, hour, minute, and second values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> mdy_hms("06/15/2023 08:30:15")
2023-06-15T08:30:15

julia> mdy_hms("06.15.2023.08.30.15")
2023-06-15T08:30:15

julia> mdy_hms("06.15.2023.08.30.15 pm")
2023-06-15T20:30:15

julia> mdy_hms("06152023083015")
2023-06-15T08:30:15

julia> mdy_hms(missing)
missing
```
