```
mdy_hm(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "MM-DD-YYYY HH:MM" to a DateTime object.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed month, day, year, and hour values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> mdy_hm("06-15-2023 09:03 P")
2023-06-15T21:03:00

julia> mdy_hm("june 15 2023 09:03 p")
2023-06-15T21:03:00

julia> mdy_hm("06-15-2023 09:03 ")
2023-06-15T09:03:00

julia> mdy_hm("june 15 2023 09:03 p")
2023-06-15T21:03:00

julia> mdy_hm(missing)
missing
```
