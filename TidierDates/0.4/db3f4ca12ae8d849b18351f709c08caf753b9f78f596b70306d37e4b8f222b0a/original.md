```
mdy_h(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "MM-DD-YYYY HH" to a DateTime object.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed month, day, year, and hour values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> mdy_h("06-15-2023 09hr")
2023-06-15T09:00:00

julia> mdy_h("06-15-2023 09hr pM")
2023-06-15T21:00:00

julia> mdy_h("jan 3 2023 09hr p")
2023-01-03T21:00:00

julia> mdy_h(missing)
missing
```
