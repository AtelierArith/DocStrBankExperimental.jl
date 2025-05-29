```
dmy_hms(datetime_string::Union{AbstractString, Missing})
```

Convert a string with "Day-Month-Year Hour:Minute:Second" format to a DateTime object.

# Arguments

`datetime_string`: A string (can contain missing values in a DataFrame).

# Returns

A DateTime object converted from the string. If the input is missing or the string format is incorrect, the function returns a missing value.

# Examples

```jldoctest
julia> dmy_hms("15-06-2023 09:30:00")
2023-06-15T09:30:00

julia> dmy_hms("15/06/2023 09:30:00pm")
2023-06-15T21:30:00

julia> dmy_hms("15 jan 2023 09:30:00 p")
2023-01-15T21:30:00

julia> dmy_hms(missing)
missing
```
