```
hm(time_string::Union{AbstractString, Missing})::Time
```

Converts a time string in the format "HH:MM" to a Time object.

# Arguments

`time_string`: A string containing a time representation. 

# Returns

A Time object constructed from the parsed hour and minute values from the input string, if all can be parsed successfully. Returns a missing value if the input is missing or if the time information cannot be parsed from the string.

# Examples

```jldoctest
julia> hm("09:30")
09:30:00

julia> hm("12:60")
missing
```
