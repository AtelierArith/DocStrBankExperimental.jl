```
dmy_hm(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "DD-MM-YYYY HH:MM" to a DateTime object.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed day, month, year, hour, and minute values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.

# Examples

```jldoctest
julia> dmy_hm("01/01/2020 4:30PM")
2020-01-01T16:30:00

julia> dmy_hm("01/01/2020 4:30 a")
2020-01-01T04:30:00

julia> dmy_hm(missing)
missing
```
