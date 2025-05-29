```
dmy(date_string::Union{AbstractString, Missing})
```

Converts a date string in various formats (like "ddmmyyyy", "day month, year", "d/m/y", "d-m-y" or "day of month, year") to a Julia Date object. The function is able to handle missing values and returns missing for missing inputs.

# Arguments

`date_string`::Union{AbstractString, Missing}: The date string to be converted to a Date object.

# Examples

```jldoctest
julia> dmy("03122020")
2020-12-03

julia> dmy("3 December, 2020")
2020-12-03

julia> dmy("23/12/2020")
2020-12-23

julia> dmy("3-12-2020")
2020-12-03

julia> dmy("3rd of December, 2020")
2020-12-03

julia> dmy("3rd of December, 2020")
2020-12-03

julia> dmy(missing)
missing
```
