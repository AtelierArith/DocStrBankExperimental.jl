```
dmy_h(datetime_string::Union{AbstractString, Missing})::DateTime
```

Converts a date and time string in the format "DD-MM-YYYY HH" to a DateTime object.

# Arguments

`datetime_string`: A string containing a datetime representation (can contain missing values in a DataFrame).

# Returns

A DateTime object constructed from the parsed day, month, year, and hour values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the datetime information cannot be parsed from the string.  

# Examples

```jldoctest
julia> dmy_h("01/01/2020 4PM")
2020-01-01T16:00:00

julia> dmy_h("01-01-2020 16hrs")
2020-01-01T16:00:00

julia> dmy_h(missing)
missing
```
