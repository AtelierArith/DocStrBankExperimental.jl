```
hms(time_string::Union{String, Missing})
```

Converts a time string in the format "HH:MM:SS" to a Time object. If the input string does not match this format or cannot be converted, an error is thrown.

# Arguments

`time_string`: A string or missing value representing a time. The string should be in the format "HH:MM:SS". Returns A Time object representing the input time string.

# Examples

```jldoctest
julia> hms("12:34:56")
12:34:56

julia> hms(missing)
missing
```
